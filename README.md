# Assignment-6

#include "iostream"
using namespace std;


class Transaction
{
public:
	int USERID;
	int Amount;
	virtual void Report()	//modify for each transaction type
	{

	}

	virtual void Perform()	//modify for each transaction type
	{

	}

};


class Transfer : public Transaction
{
public:
	int transID;   // id of the user to tranfer with
	int transType; // type of transition; to or fro

	void Perform()
	{
		cout << "\n" << "Transfer" << "\n\n";
		cout << "Enter the id of the user to tranfer with: ";
		cin >> transID;
		cout << "\n" << "Transfer type:" << "\n" << "1: To   2: Fro" << "\n";
		cin >> transType;
		if (transType == 2)
		{
			int temp = transID;
			transID = USERID;
			USERID = temp;
		}
		cout << "\n" << "Enter the amount you wish to withdraw: ";
		cin >> Amount;

	}

	void Report()
	{
		cout << "\n\n" << "Transfer of " << Amount << "$ from user: #" << USERID << " to the user: #" << transID;
	}

};


class Withdraw : public Transaction
{
public:

	void Perform()
	{
		cout << "\n" << "Withdraw" << "\n\n";
		cout << "Enter the amount you wish to withdraw: ";
		cin >> Amount;

	}
	void Report()
	{
		cout << "\n\n" << "Withdrawl of: " << Amount << "$";
	}

};

class Deposit : public Transaction
{
public:

	void Perform()
	{
		cout << "\n" << "Deposit" << "\n";
		cout << "Enter the amount you wish to deposit: ";
		cin >> Amount;
	}
	void Report()
	{
		cout << "\n\n" << "Deposit of: " << Amount << "$";
	}

};




class User
{
public:
	int ID;
	int numTrans;
	Transaction* t[100];
	int TYPE;

	User()
	{
		numTrans = 0;
	}

	void AddWithdraw()
	{
		t[numTrans] = new Withdraw;
		numTrans++;
	}

	void AddDeposit()
	{
		t[numTrans] = new Deposit;
		numTrans++;
	}

	void AddTransfer()
	{
		t[numTrans] = new Transfer;
		numTrans++;
	}

};


void main()
{
	User*u[100];
	int id;
	int type;
	int counter;

	counter = 0;

	for (int i = 0; i <= 100; i++)
	{
		u[i] = new User;
	}

	while (true)
	{
		type = 0;

		cout << "\nPlease enter your ID: ";
		cin >> id;

		cout << "\n" << "Which transaction would you like to perform" << "\n" << "1: Withdraw" << "\n" << "2: Deposit" << "\n" << "3: Transfer" << "\n";
		cin >> type;

		if (type != 1 && type != 2 && type != 3)
		{
			type = 1;
		}

		for (int i = 0; i <= counter; i++)
		{
			if (u[i]->ID == id || i == counter)
			{

			}
		}

		// Report all of the previous transactions
		counter++;

	}



}
