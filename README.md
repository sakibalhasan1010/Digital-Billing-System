//Digital-Billing-System
#include <iostream>
#include <conio.h>
#include <fstream>

using namespace std;

class bill// main class
{
private:   // variables
    int code;
    float price;
    float discount;
    string name;

public: //function
    void menu();
    void admin();
    void customer();
    void add();

};

void bill::menu() // difine menu function of bill class
{
   // p:
    system("cls");
    int choice;
    char ch;
    string email,pass;
    cout<<"\n\n\n\t\t\tControl Panel";
    cout<<"\n\n 1.Admin";
    cout<<"\n\n 2.Customer";
    cout<<"\n\n 3.Exit";
    cout<<"\n\n Enter Your Choice: ";
    cin>>choice;

    switch(choice)
    {
    case 1:
         //sytem("cls");
         cout<<"\n\n\t\t\tLogin System";
         cout<<"\n\n E-mail : ";
         cin>>email;
         cout<<"\n\n Password : ";

         for(int i=1; i<=6; i++){
            ch = getch();
            pass += ch;
            cout<<"*";
         }

         if( email == "sakib@gmail.com" && pass == "sakibb")
         {
           admin();
         }
        else{
            cout<<"\n\n Wrong email and password...Please try again.";
        }
        break;

    case 2:
        customer();

    case 3:
        exit(0);
    default:
        cout<<"\n\n Wrong value...Please try again.";



    }
    getch();
    //goto p;

}
void bill::admin()  //admin function of bill class
{
    //P:
    system("cls");
    int choice;
    cout<<"\n\n\t\t\tAdmin Panel";
    cout<<"\n\n 1.Add Product";
    cout<<"\n\n 2.Search Product";
    cout<<"\n\n 3.Edit Product";
    cout<<"\n\n 4.Delete Product";
    cout<<"\n\n 5.Show Product";
    cout<<"\n\n 6.Go Back";
    cout<<"\n\n Enter Your Choice: ";
    cin>>choice;
    switch(choice)
    {
    case 1:
        add();
        break;
    case 2:
        break;
     case 3:
        break;
    case 4:
        break;
    case 5:
        break;
    case 6:
        menu();
    default:
        cout<<"\n\n Wrong Value...Plese try again.";
    }

    getch();
   // goto p;

}

 void bill::customer()  //Customer function of bill calss
 {
    //p:
    system("cls");
    int choice;
    cout<<"\n\n\t\t\tCustomer Panel";
    cout<<"\n\n 1. Sale Product";
    cout<<"\n 2. Go Back";
    cout<<"Enter Your Choice: ";
    cin>>choice;
    switch(choice)
    {
    case 1:
        break;
    case 2:
        menu();
    default:
        cout<<"\n\n wrong Value...Please try again.";
    }
    getch();
   // goto p;


 }

 void bill::add()  //add product function of bill class
{
  p:
  system("cls");
  fstream file;
  int c,found=0;
  float p,d;
  string n;
  cout<<"\n\n\t\t\tAdd New Product";
  cout<<"\n\n product Code : ";
  cin>>code;
  cout<<"\n\n Name : ";
  cin>>name;
  cout<<"\n\n Price : ";
  cin>>price;
  cout<<"\n\n Discount in % : ";
  cin>>discount;
  file.open("product.txt",ios::in);
  if(!file){
   file.open("product.txt",ios::app|ios::out);
   file<<" "<<code<<" "<<name<<" "<<price<<" "<<discount<<"\n";
   file.close();
  }
  else{


  file>>c>>n>>p>>d;
  while(!file.eof()){
        if(c == code)
        {
            found++;
        }
    file>>c>>n>>p>>d;

   }
    file.close();
    if(found == 1){
        goto p;
    }
    else{
        file.open("product.txt",ios::app|ios::out);
        file<<" "<<code<<" "<<name<<" "<<price<<" "<<discount<<"\n";
        file.close();
    }
  }
}

int main()
{
     bill b;
     b.menu();

}


