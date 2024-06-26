# MyToken Smart Contract

## Overview

MyToken is a simple Ethereum smart contract that implements a basic ERC20-like token with minting and burning functionalities. The contract allows the creation and destruction of tokens, and tracks balances for different addresses.

## Requirements

The contract has the following features:
1. Public variables to store details about the token:
   - Token Name: "META"
   - Token Abbreviation: "MTA"
   - Total Supply

2. A mapping to store the balance of each address.

3. A `mint` function to create new tokens and assign them to an address.

4. A `burn` function to destroy tokens from an address.

5. Conditionals in the `burn` function to ensure that the balance of the address is sufficient to burn the desired amount.

## Contract Details

### Public Variables

- `string public tokenName = "META";`
- `string public tokenAbbr = "MTA";`
- `uint public totalSupply = 0;`

These variables store the name, abbreviation, and total supply of the token.

### Mapping

- `mapping (address => uint) public balances;`

This mapping keeps track of the token balance for each address.

### Mint Function

```solidity
function mint(address _address, uint _value) public {
    totalSupply += _value;
    balances[_address] += _value;
}
```

The `mint` function increases the total supply of the token by `_value` and adds the same amount to the balance of `_address`.

### Burn Function

```solidity
function burn(address _address, uint _value) public {
    if(balances[_address] >= _value) {
        totalSupply -= _value;
        balances[_address] -= _value;
    }
}
```

The `burn` function decreases the total supply of the token by `_value` and deducts the same amount from the balance of `_address`. The function includes a conditional check to ensure that the address has enough balance to burn the specified amount of tokens.

## How to Use

### Deploying the Contract

1. Deploy the `MyToken` contract to the Ethereum blockchain using a compatible development environment such as Remix, Truffle, or Hardhat.

### Interacting with the Contract

1. **Minting Tokens**:
   - Call the `mint` function with the desired address and the amount of tokens to mint. For example:
     ```solidity
     mint(0xYourAddress, 1000);
     ```

2. **Burning Tokens**:
   - Call the `burn` function with the desired address and the amount of tokens to burn. Ensure the address has sufficient balance. For example:
     ```solidity
     burn(0xYourAddress, 500);
     ```

### Viewing Balances

- You can view the balance of any address by calling the `balances` mapping with the address. For example:
  ```solidity
  balances(0xYourAddress);
  ```

### License

This project is licensed under the MIT License. See the LICENSE file for details.

## Conclusion

MyToken provides a simple implementation of a token with minting and burning capabilities. This can be used as a basic template for more complex token contracts or as a learning tool for understanding basic token operations on the Ethereum blockchain.
