#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_ACCOUNTS 100
#define MAX_TRANSACTIONS 50

typedef struct {
    char type[10];
    float amount;
} Transaction;

typedef struct {
    int accountNumber;
    char name[50];
    float balance;
    Transaction transactions[MAX_TRANSACTIONS];
    int transactionCount;
} Account;

Account accounts[MAX_ACCOUNTS];
int accountCount = 0;

void createAccount() {
    if (accountCount >= MAX_ACCOUNTS) {
        printf("Cannot create more accounts.\n");
        return;
    }

    Account newAccount;
    newAccount.accountNumber = accountCount + 1;
    printf("Enter your name: ");
    scanf(" %[^\n]", newAccount.name);
    newAccount.balance = 0;
    newAccount.transactionCount = 0;

    accounts[accountCount++] = newAccount;
    printf("Account created successfully! Your account number is %d\n", newAccount.accountNumber);
}

void depositMoney() {
    int accNum;
    float amount;
    printf("Enter account number: ");
    scanf("%d", &accNum);

    if (accNum < 1 || accNum > accountCount) {
        printf("Invalid account number.\n");
        return;
    }

    printf("Enter amount to deposit: ");
    scanf("%f", &amount);

    if (amount <= 0) {
        printf("Amount must be greater than 0.\n");
        return;
    }

    accounts[accNum - 1].balance += amount;
    strcpy(accounts[accNum - 1].transactions[accounts[accNum - 1].transactionCount].type, "Deposit");
    accounts[accNum - 1].transactions[accounts[accNum - 1].transactionCount++].amount = amount;

    printf("Amount deposited successfully! Current balance: %.2f\n", accounts[accNum - 1].balance);
}

void withdrawMoney() {
    int accNum;
    float amount;
    printf("Enter account number: ");
    scanf("%d", &accNum);

    if (accNum < 1 || accNum > accountCount) {
        printf("Invalid account number.\n");
        return;
    }

    printf("Enter amount to withdraw: ");
    scanf("%f", &amount);

    if (amount <= 0 || amount > accounts[accNum - 1].balance) {
        printf("Invalid amount. Insufficient balance.\n");
        return;
    }

    accounts[accNum - 1].balance -= amount;
    strcpy(accounts[accNum - 1].transactions[accounts[accNum - 1].transactionCount].type, "Withdrawal");
    accounts[accNum - 1].transactions[accounts[accNum - 1].transactionCount++].amount = amount;

    printf("Amount withdrawn successfully! Current balance: %.2f\n", accounts[accNum - 1].balance);
}

void displayAccountDetails() {
    int accNum;
    printf("Enter account number: ");
    scanf("%d", &accNum);

    if (accNum < 1 || accNum > accountCount) {
        printf("Invalid account number.\n");
        return;
    }

    Account acc = accounts[accNum - 1];
    printf("\n--- Account Details ---\n");
    printf("Account Number: %d\n", acc.accountNumber);
    printf("Name: %s\n", acc.name);
    printf("Balance: %.2f\n", acc.balance);
}

void generateMiniStatement() {
    int accNum;
    printf("Enter account number: ");
    scanf("%d", &accNum);

    if (accNum < 1 || accNum > accountCount) {
        printf("Invalid account number.\n");
        return;
    }

    Account acc = accounts[accNum - 1];
    printf("\n--- Mini Statement ---\n");
    printf("Account Number: %d\n", acc.accountNumber);
    printf("Name: %s\n", acc.name);
    printf("Balance: %.2f\n", acc.balance);
    printf("Transactions:\n");

    for (int i = 0; i < acc.transactionCount; i++) {
        printf("%s: %.2f\n", acc.transactions[i].type, acc.transactions[i].amount);
    }
}

int main() {
    int choice;
    do {
        printf("\n--- Bank Account Management System ---\n");
        printf("1. Create Account\n");
        printf("2. Deposit Money\n");
        printf("3. Withdraw Money\n");
        printf("4. Display Account Details\n");
        printf("5. Generate Mini Statement\n");
        printf("6. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                createAccount();
                break;
            case 2:
                depositMoney();
                break;
            case 3:
                withdrawMoney();
                break;
            case 4:
                displayAccountDetails();
                break;
            case 5:
                generateMiniStatement();
                break;
            case 6:
                printf("Exiting the system. Thank you!\n");
                break;
            default:
                printf("Invalid choice. Try again.\n");
        }
    } while (choice != 6);

    return 0;
}