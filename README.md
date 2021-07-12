# Proof of Authority Development Chain

![blockchain1](https://www.epiqglobal.com/epiq/media/thinking/blog/Epiq_Angle_blockchain_hack_680x340.jpg)

## Using digital money for ZBank experiment. 

Assign to show how effective the use of the Blockchain Technology can be in the banking world, I pledged to create a genesis block from scratch, connected to two nodes using geth, and then is used to mine for Ethereum.  Usign MyCrypto I then linked the two test nodes to simulate transactions from my mining node using their public addresses .

---
### The process:
#### 1. Create accounts for nodes with a separate "datadir" for each using Geth:
Geth is installed in my jupyterlab-workplace local directory. Accessing Geth from my local directory and using:

    ./geth account new --datadir bpmnode1
    
Screenshot shows the resposnse confirming the account confirmation:
![bpmnode1](https://raw.githubusercontent.com/sheldonpalm69/Proof-Of-Authority-Blockchain/main/Screenshots/puppeth%20name.png)

The proceedure is repeated for the second node:

    ./geth account new --datadir bpmnode2

Below confiration places us in a position to proceed to creating the block for our demonstration.

#### 2. Use ./puppeth in Geth to configure a new genesis block:
It is important to select the followings to create the block. Using the two public addresses, generated in step 1, when it asks which accounts you want to seal and which should be pre-funded. The chain ID, secured with a password, selecting the level of wei in order to get the block ready for mining. 

![blockname](https://raw.githubusercontent.com/sheldonpalm69/Proof-Of-Authority-Blockchain/main/Screenshots/puppeth%20name.png))

#### 3. Export genesis configuration:
The below results in the confirmtion of the creation of the gensis block, which is saved in the Proof Of Authority Blockchain Folder, bpmbank.json

##### 4. Ctrl+C to exit Puppeth and use geth command to initialize each node and connect to your genesis block (my network name was bpmbank):

    ./geth init bpmbank.json --datadir bpmnode1
    ./geth init bpmbank.json --datadir bpmnode2

![config](https://raw.githubusercontent.com/sheldonpalm69/Proof-Of-Authority-Blockchain/main/Screenshots/node%20init.png)

The genisis block is now initialize and ready for mining


#### 5. Enable mining:

    ./geth --datadir bpmnode1 --unlock "0x4a81389E419ff4fF937C140f80E3a9632d0f5dd5" --mine --rpc --allow-insecure-unlock
    
Below is a screenshot of the terminal confirmation of the block initializing mining:
![mining1](https://raw.githubusercontent.com/sheldonpalm69/Proof-Of-Authority-Blockchain/main/Screenshots/node%20init2.png)

In a new terminal window, cd into your directory, and launch the second node, passing in the enode address of the first node:

    ./geth --datadir bpmnode2 --unlock "0xa137E24C11B44b7feeB4d834Cfd4965599ed3dDB" --mine --port 30304 --bootnodes "enode://e02b9a1ecb1f254f984aeb4c51d0c154ababe825c09d1b5c5d9669e946e07f8feb43940b901382f10a6adcf172ac1d994e8dcaf673ee47c9dbec22255bd74df6@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock
    
Screenshot below is response:
![mining2](https://raw.githubusercontent.com/sheldonpalm69/Proof-Of-Authority-Blockchain/main/Screenshots/node2%20mine.png)

#### 6. MyCrypto test transaction using a custom node:
Set up a custom node "bpmbank" in MyCrypto, identifying ETH as the currency and setting your Chain ID to he one used in the genisis block.  Connect the custom node and access the balance with Keystore File:
    UTC--2021-07-12T02-09-27.994470700Z--4a81389e419ff4ffxxxx140f80e3a9632d0f5dd5

![custom_node](https://raw.githubusercontent.com/sheldonpalm69/Proof-Of-Authority-Blockchain/main/Screenshots/MyCrypto.jpg)

#### 7. Test send transaction:
Send my self 15000 ETH by using my first node  address as the address to send Ethereum to.  Screenshots are confimation of the process:

Account access
![MyCrypto](/Screenshots/mycrypto.png?raw=true)
Setting up transaction
![confirmation](https://raw.githubusercontent.com/sheldonpalm69/Proof-Of-Authority-Blockchain/main/Screenshots/MyCrypto_on%20bpmbanknode.png)
15000ETH
![confirmation2](https://raw.githubusercontent.com/sheldonpalm69/Proof-Of-Authority-Blockchain/main/Screenshots/transaction1.png)
bpmbank custom node selected and connected.
![confirmation2](https://raw.githubusercontent.com/sheldonpalm69/Proof-Of-Authority-Blockchain/main/Screenshots/transaction1_LI.jpg)
Confirmed transaction processed for mining in the block
![confirmation2](https://raw.githubusercontent.com/sheldonpalm69/Proof-Of-Authority-Blockchain/main/Screenshots/transfer1%20in%20mine.png)
Confirmation stamp from MyCrypto
![confirmation2](https://raw.githubusercontent.com/sheldonpalm69/Proof-Of-Authority-Blockchain/main/Screenshots/transfer2.png)
