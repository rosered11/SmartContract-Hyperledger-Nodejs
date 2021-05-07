# SmartContract-Hyperledger-Nodejs

## Blockchain

### Distributed Ledgers, Transactions and Chaincode

- Chaincode will be encapsulate this business logic or transaction are recorded in a ledger.
These recorded transactions are immutable not as they cann't be updated or deleted.

**Chaincode**

Chaincode implements the business logic and exposes the state management features by way of one or more functions,
and these functions are executed from the application by way of transactions.



- Exposes one or more functions
    - Applications execute functions by way of Transactions
    - Functions exposed for reading the state

**Client Side API**

Chaincode deployed on the peer. Applications use fabric client as the case for interacting with the Chaincode.
There are two api that are used by the applications.

- **Invoke** API is used for executing the business logic in the chaincode by way of transactions.
- **Query** API is used for reading the state of the assets from the distributed ledger platform.

Both **Invoke** and **Query** API execute the functions exposed by the chaincode.

The client side api execute the functions by passing **JsonObject** to the chaincode.

The Json object has one attribute called **Args**, which is set to an array of string types.

```
{
    Args: [func, paranm-1, param-2]
}
```

The first element in the of array is the function name, which is executed by the chaincode.

The difference is that when you execute the fucntion in the chaincode by way of **Invoke** the transaction gets recorded in the **ledger** whereas when you use the **Query** the transaction is not recoreded in the **ledger**

In effect though both **Invoke** and **Query** lead to the execution of function on the chaincode the flow of transaction is not the same.

When the client to execute the **Invoke** transaction proposal is created and it is sent to the **Endorsing peer**.
If everything is good with the transaction proposal the Endorsing peer **signed** the transaction proposal and send it back to the **client**.
The client then sends the same transaction proposal to the **Orderers** for including the transaction in the **Block order**.
At some point creates the block that the transaction included and then sends it accross to the peer in the next **Block**

One thing you will observe here in this iLLustration is that not all of the peers have the chaincode deployed.
So the message here is that even if the peer doesn't have the chaincode that led to the creation of the transaction,
it will still receive the block with the transaction.
In the case of Query api invocation declined. Execute the query function on any of the peer that has the chaincode deployed.

## Tools



## Reference

- [Top 6 Blockchain Frameworks to Build Your App](https://rubygarage.org/blog/best-blockchain-frameworks)

- [สร้าง Blockchain ด้วย Hyperledger : #4 การเขียน NodeJS Application บน Fabric](https://medium.com/@methuz/%E0%B8%AA%E0%B8%A3%E0%B9%89%E0%B8%B2%E0%B8%87-blockchain-%E0%B8%94%E0%B9%89%E0%B8%A7%E0%B8%A2-hyperledger-4-%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%80%E0%B8%82%E0%B8%B5%E0%B8%A2%E0%B8%99-nodejs-application-%E0%B8%9A%E0%B8%99-fabric-26b265cd8743)

- [Hyperledger Fabric (HLF) - How to use the Node.js SDK? : Hyperledger Sweden Study Circle](https://www.youtube.com/watch?v=I4i-LwLoznA)