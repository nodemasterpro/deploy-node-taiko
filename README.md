# Deploy Taiko Hekla Node
Join the cutting-edge of Ethereum scalability solutions with the Taiko Hekla testnet. Taiko offers a Layer 2 scalability solution that integrates seamlessly with Ethereum, leveraging ZK Rollups to enhance transaction speed and reduce fees without compromising on decentralization or security.

## Prerequisites
Linux Ubuntu 22.04 LTS with Docker and Docker-compose installed
Minimum of 2 CPU cores (4 cores recommended)
At least 4 GB RAM (16 GB recommended)
1 TB of free storage space
For optimal performance, using a Contabo VPS 3 server is advised due to its reliability and robustness, perfectly meeting the technical requirements for running a Taiko node.

## Preparing Your Environment
Before you begin the installation of a Taiko node, ensure your system is ready and all necessary software is installed:

```
sudo apt update && sudo apt upgrade -y
sudo apt install docker-ce docker-compose git -y
```

## Setting Up Your Taiko Metamask Wallet
To participate in the Taiko consensus, you'll need a Metamask wallet equipped with a private key. If you already have a wallet from a previous Katla node, you can reuse it. Ensure it's added to the Ethereum testnet Holesky network and funded via the Holesky faucet.

## Downloading the Project
Clone the Taiko project repository to access the Ansible playbook and all required files:

```
git clone https://github.com/taikoxyz/simple-taiko-node.git
cd simple-taiko-node
```

## Installation of the Holesky Node
Initiate the installation of your Holesky node using this command, entering the necessary network and wallet information when prompted:

```
ansible-playbook install_holesky_node.yml
```

## Installation of the Taiko Node
Initiate the installation of your Taiko node using this command, entering the necessary network and wallet information when prompted:

```
ansible-playbook install_taiko_node.yml
```
Ensure you have the following details ready:

L1_ENDPOINT_HTTP: The Blockpi HTTP API URL for the Holesky testnet, obtainable from the Blockpi website.
L1_ENDPOINT_WSS: The WebSocket API URL for the Holesky testnet, also from Blockpi.
PROPOSER_PRIVATE_KEY: Your dedicated Taiko Metamask account's private key.

## Starting the Taiko Node Service
After setting up your node, start the Taiko node service:

```
sudo systemctl start taiko-node
```

## Monitoring Node Activity
Monitor your Taiko node's activity and ensure it synchronizes with the main blockchain:

```
journalctl -u taiko-node -f -o cat
```
Check the synchronization status on the Grafana dashboard at http://<IP_OF_YOUR_VPS>:3001/d/L2ExecutionEngine/l2-execution-engine-overview.

## Retrieving Funds
Once your node is synchronized, retrieve any funds mined during setup from the Holesky faucet and ensure they've arrived in your wallet.

## Additional Commands
### Stopping the Holesky Node
```
su - ethuser
cd eth-docker
./ethd down
exit
```

### Stopping the Taiko Node
```
sudo systemctl stop taiko-node
```

### Starting the Holesky Node
```
su - ethuser
cd eth-docker
./ethd up
exit
```

### Starting the Taiko Node
```
sudo systemctl start taiko-node
```

### Removing the Taiko Node
To completely remove your Holesky node, rerun the playbook with the removal action set:

```
ansible-playbook remove_holesky_node.yml
```


To completely remove your Taiko node, rerun the playbook with the removal action set:

```
ansible-playbook remove_taiko_node.yml
```
Join the Taiko community on Discord and Twitter to stay informed and connect with other users. For any questions, feel free to reach out on my Discord.