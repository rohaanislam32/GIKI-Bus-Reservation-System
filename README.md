#include <iostream>
#include <fstream>

using namespace std;

class Bus {
private:
    string name;
    string regNumber;
    string city;
    string ticketType;
    string paymentMethod;

public:
    void reserveTicket() {
        cout << "Welcome to the Bus Reservation System!\n";
        cout << "Enter your name: ";
        cin.ignore();
        getline(cin, name);

        cout << "Enter your registration number: ";
        cin >> regNumber;

        cout << "Available cities: Lahore, Islamabad, Peshawar\n";
        cout << "Enter the city you want to go to: ";
        cin.ignore();
        getline(cin, city);

        cout << "Choose ticket type:\n";
        cout << "1. One-way ticket\n";
        cout << "2. Return ticket\n";
        int ticketChoice;
        cout << "Enter your choice (1 or 2): ";
        cin >> ticketChoice;

        if (ticketChoice == 1) {
            ticketType = "One-way";
        } else if (ticketChoice == 2) {
            ticketType = "Return";
        } else {
            cout << "Invalid choice. Please try again.\n";
            return;
        }

        cout << "Choose payment method:\n";
        cout << "1. Cash\n";
        cout << "2. Online\n";
        int paymentChoice;
        cout << "Enter your choice (1 or 2): ";
        cin >> paymentChoice;

        if (paymentChoice == 1) {
            paymentMethod = "Cash";
        } else if (paymentChoice == 2) {
            paymentMethod = "Online";
        } else {
            cout << "Invalid choice. Please try again.\n";
            return;
        }

        saveReservation();
        cout << "Ticket reserved successfully!\n";
    }

private:
    void saveReservation() {
        ofstream file("reservations.txt", ios::app);
        if (file.is_open()) {
            file << "Name: " << name << ", Reg Number: " << regNumber << endl;
            file << "City: " << city << ", Ticket Type: " << ticketType << ", Payment Method: " << paymentMethod << endl;
            file.close();
        } else {
            cout << "Failed to save reservation.\n";
        }
    }
};

int main() {
    Bus bus;
    bus.reserveTicket();
    return 0;
}
