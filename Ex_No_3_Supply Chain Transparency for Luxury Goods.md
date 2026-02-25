# Ex_No_3_Supply Chain Transparency for Luxury Goods
### NAME: SATHYANARAYANAN M
### REGISTER NUMBER: 212224040300
### DATE : 24.02.25
## Aim:
To develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
## Algorithm:
The manufacturer records product creation details on-chain.


The product moves through different supply chain checkpoints.


The ownership of the product can be transferred securely.


Buyers can verify the product’s authenticity.


## Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LuxurySupplyChain {
    struct Product {
        string name;
        address currentOwner;
        bool verified;
    }

    mapping(uint256 => Product) public products;

    event ProductRegistered(uint256 productId, string name);
    event OwnershipTransferred(uint256 productId, address newOwner);

    function registerProduct(uint256 productId, string memory name) public {
        require(products[productId].currentOwner == address(0), "Product already registered");
        products[productId] = Product(name, msg.sender, true);
        emit ProductRegistered(productId, name);
    }

    function transferOwnership(uint256 productId, address newOwner) public {
        require(products[productId].currentOwner == msg.sender, "Not the owner");
        products[productId].currentOwner = newOwner;
        emit OwnershipTransferred(productId, newOwner);
    }

    function verifyProduct(uint256 productId) public view returns (string memory, address, bool) {
        Product memory p = products[productId];
        return (p.name, p.currentOwner, p.verified);
    }
}
```
## Expected Output:
A luxury good (e.g., a Rolex watch) is registered on-chain.
<img width="1914" height="1138" alt="image" src="https://github.com/user-attachments/assets/b5a3f388-8707-4199-9f7f-42c09cfa9cb4" />
<img width="1909" height="1108" alt="image" src="https://github.com/user-attachments/assets/fb2e0974-6389-4819-a418-328bd8b3a148" />
<img width="1915" height="1097" alt="image" src="https://github.com/user-attachments/assets/50248e9f-77d3-426f-828a-b4e004a9322b" />



Ownership is transferred at every checkpoint.


Buyers can check the authenticity before purchasing.


## High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.

## RESULT : 
Thus a smart contract that tracks the supply chain of luxury goods, ensuring authenticity is executed successfully.
