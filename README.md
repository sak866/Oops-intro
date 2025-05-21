# Oops-intro
1.1) Create a class Person with properties (name and age) with following features
a. Default age of person should be 18;

b. A person object can be initialized with name and age,

c. Method to display name and age of person

public class Person {
    private String name;
    private int age;

    public Person() {
        this.age = 18;
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void display() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
    }
}
1.2) Create class Product (pid, price, quantity) with parameterized constructor. Create a main function in different class (say ProductMain) and perform following task:

a. Accept five product information from user and store in an array

b. Find Pid of the product with the highest price.

c. Create method (with array of product’s object as argument) in ProductMain class to

calculate and return the total amount spent on all products. (amount spent on

single product-price of product quantity of product

public class Product {
    int pid;
    double price;
    int quantity;

    public Product(int pid, double price, int quantity) {
        this.pid = pid;
        this.price = price;
        this.quantity = quantity;
    }
}
import java.util.Scanner;

public class ProductMain {

    public static double calculateTotalAmount(Product[] products) {
        double total = 0;
        for (Product p : products) {
            total += p.price * p.quantity;
        }
        return total;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Product[] products = new Product[5];

        for (int i = 0; i < products.length; i++) {
            System.out.println("Enter product " + (i+1) + " details (pid, price, quantity): ");
            int pid = sc.nextInt();
            double price = sc.nextDouble();
            int quantity = sc.nextInt();
            products[i] = new Product(pid, price, quantity);
        }

        double maxPrice = products[0].price;
        int maxPricePid = products[0].pid;
        for (Product p : products) {
            if (p.price > maxPrice) {
                maxPrice = p.price;
                maxPricePid = p.pid;
            }
        }
        System.out.println("Product ID with highest price: " + maxPricePid);

        double totalAmount = calculateTotalAmount(products);
        System.out.println("Total amount spent on all products: " + totalAmount);

        sc.close();
    }
}
1.3) Create Class Account with data member as Balance. Create two constructors (no argument, and with argument) and perform following task

a. method to deposit the amount to the account

b. method to withdraw the amount from the account

c. method to display the Balance

public class Account {
    private double balance;

    public Account() {
        balance = 0.0;
    }

    public Account(double initialBalance) {
        balance = initialBalance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: " + amount);
        } else {
            System.out.println("Invalid deposit amount");
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrawn: " + amount);
        } else {
            System.out.println("Invalid withdraw amount or insufficient balance");
        }
    }

    public void displayBalance() {
        System.out.println("Current Balance: " + balance);
    }
}
1.4) Define a base class Person with attributes name and age.

Create a subclass Employee that inherits from Person and adds attributes like employeeID and salary

// Person

public class Person {
    protected String name;
    protected int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
public class Employee extends Person {
    private int employeeID;
    private double salary;

    public Employee(String name, int age, int employeeID, double salary) {
        super(name, age);
        this.employeeID = employeeID;
        this.salary = salary;
    }

    public void displayEmployee() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Employee ID: " + employeeID);
        System.out.println("Salary: " + salary);
    }
}


