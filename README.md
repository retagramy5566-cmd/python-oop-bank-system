# python-oop-bank-system
Simple Python OOP project for practice
class Transaction:
  def __init__(self,amount:int,t_type:str) :
    self.amount=amount
    self.t_type=t_type
  def __str__(self):
    return f'{self.t_type}:{self.amount}'
class Account:
  def __init__(self,account_id:int) :
    self.account_id=account_id
    self.balance= 0
    self.transaction=[]
  def deposit(self,amount):
   if amount>0:
     self.balance+=amount
     tan=Transaction(amount,'deposit')
     self.transaction.append(tan)

   else:
    print(f"this is {amount} is invalid num")
  def withdraw(self,amount) :
    if amount<= self.balance:
       self.balance-=amount
       tan=Transaction(amount,'withdraw')
       self.transaction.append(tan)
    else:
      print(f' {self.balance} less than {amount} the proccess error ')
  def  get_total_transactions_amount(self):
      total=0
      for t in self.transaction:
        total+= t.amount

      print(total)
class Customer:
  def __init__(self,name,customer_id):
    self.name=name
    self.customer_id=customer_id
    self.accounts=[]
  def add_account(self,account:Account) :
    self.accounts.append(account) 
  def list_accounts(self) :
    print(self.accounts) 
  def __str__(self):
    return f"{self.name}"

tran=Transaction(98,'deposite')
tran.__str__()
ac=Account(95)
ac.deposit(1200)
ac.deposit(300)
ac.withdraw(200)
ac.withdraw(3000)
ac.get_total_transactions_amount()
customer=Customer('retaj',405)
customer.add_account(ac)
customer.list_accounts()
customer.__str__()
