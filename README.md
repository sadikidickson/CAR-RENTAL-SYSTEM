# CAR-RENTAL-SYSTEM# Car Rental System

## Overview

This project is a simple car rental system implemented in Java. It manages vehicles, clients, and rental transactions. The system allows adding new vehicles and clients, renting out vehicles to clients, and returning rented vehicles. It also tracks the rental history of each client.

## Features

- Add new vehicles to the rental service.
- Add new clients to the rental service.
- Rent out vehicles to clients.
- Return rented vehicles.
- View available vehicles.
- View rental history for clients.
- Validate client license numbers.

## Classes

### Vehicle

Represents a vehicle in the rental agency.

#### Attributes

- `plateNumber` (String): The vehicle's plate number.
- `carModel` (String): The model of the car.
- `rentedStatus` (boolean): Indicates if the car is currently rented.
- `year` (int): The year the car was manufactured.
- `color` (String): The color of the car.
- `mileage` (int): The mileage of the car.

#### Methods

- `Vehicle(String plateNumber, String carModel, int year, String color, int mileage)`: Constructor to initialize a vehicle.
- `String getPlateNumber()`: Returns the plate number.
- `String getCarModel()`: Returns the car model.
- `boolean isRented()`: Checks if the vehicle is rented.
- `void rentOut()`: Marks the vehicle as rented.
- `void returnVehicle()`: Marks the vehicle as returned.
- `String toString()`: Returns a string representation of the vehicle.

### Client

Represents a client of the rental agency.

#### Attributes

- `fullName` (String): The client's full name.
- `licenseNumber` (String): The client's license number.
- `rentalHistory` (List<String>): A list of rental records for the client.

#### Methods

- `Client(String fullName, String licenseNumber)`: Constructor to initialize a client.
- `String getFullName()`: Returns the client's full name.
- `String getLicenseNumber()`: Returns the client's license number.
- `void addRental(String rentalRecord)`: Adds a rental record to the client's history.
- `List<String> getRentalHistory()`: Returns the client's rental history.
- `String toString()`: Returns a string representation of the client.

### RentalService

Manages the rental agency's operations.

#### Attributes

- `vehicleList` (List<Vehicle>): A list of vehicles in the rental service.
- `clientList` (List<Client>): A list of clients in the rental service.

#### Methods

- `RentalService()`: Constructor to initialize the rental service.
- `void addVehicle(Vehicle vehicle)`: Adds a vehicle to the service.
- `void addClient(Client client)`: Adds a client to the service.
- `boolean isValidLicenseNumber(String licenseNumber)`: Validates the client's license number.
- `Vehicle findAvailableVehicle(String model)`: Finds an available vehicle by model.
- `boolean rentVehicle(Client client, String model)`: Rents a vehicle to a client.
- `void returnVehicle(Client client, Vehicle vehicle)`: Returns a rented vehicle.
- `List<Vehicle> getVehicleList()`: Returns the list of vehicles.
- `List<Client> getClientList()`: Returns the list of clients.
- `List<Vehicle> getAvailableVehicles()`: Returns the list of available vehicles.
- `String toString()`: Returns a string representation of the rental service.

## How to Run

1. Ensure you have Java Development Kit (JDK) installed on your system.
2. Compile the Java files:
   ```sh
   javac -d bin src/com/mycompany/assproject1/*.java
   ```
3. Run the main class:
   ```sh
   java -cp bin com.mycompany.assproject1.ASSproject1
   ```

## Unit Tests

The unit tests are implemented using JUnit. Ensure you have JUnit set up in your environment.

1. Compile the test files along with the source files:
   ```sh
   javac -cp .:junit-5.8.1.jar:bin -d bin test/com/mycompany/assproject1/*.java
   ```
2. Run the tests:
   ```sh
   java -cp .:junit-5.8.1.jar:bin org.junit.runner.JUnitCore com.mycompany.assproject1.RentalServiceTest
   ```

## Example Usage

```java
public class ASSproject1 {
    public static void main(String[] args) {
        RentalService rentalService = new RentalService();

        rentalService.addVehicle(new Vehicle("DEF456", "Tesla Model S", 2020, "Red", 15000));
        rentalService.addVehicle(new Vehicle("GHI789", "Chevrolet Malibu", 2019, "Black", 30000));
        rentalService.addVehicle(new Vehicle("JKL012", "BMW 3 Series", 2021, "White", 10000));

        rentalService.addClient(new Client("Alice Johnson", "D9876543"));
        rentalService.addClient(new Client("Bob Brown", "D6543210"));

        Client firstClient = rentalService.getClientList().get(0);
        rentalService.rentVehicle(firstClient, "Tesla Model S");

        Vehicle rentedVehicle = rentalService.getVehicleList().get(0);
        rentalService.returnVehicle(firstClient, rentedVehicle);

        System.out.println("Available Vehicles: " + rentalService.getAvailableVehicles());
        System.out.println("Rental History for " + firstClient.getFullName() + ": " + firstClient.getRentalHistory());
        System.out.println(rentalService);
    }
}
```
