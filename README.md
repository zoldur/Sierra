# Sierra Coin
Shell script to install an [Sierra Masternode](https://www.sierracoin.net/) on a Linux server running Ubuntu 16.04. Use it on your own risk.

***
## VPS installation:
```
wget -N https://raw.githubusercontent.com/zoldur/Sierra/master/sierra_install.sh
bash sierra_install.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the Sierra Coin Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **10000** **SIERRA** to **MN1**. You need to send all 10000 coins in one single transaction.
4. Wait for 15 confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**
7. Go to  ** Tools -> "Open Masternode Configuration File"
8. Add the following entry:
```
Alias Address Privkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
12. Select your MN and click **Start Alias** to start it.
13. Alternatively, open **Debug Console** and type:
```
startmasternode alias 0 MN1
```
14. Login to your VPS and check your masternode status by running the following command to confirm your MN is running:
```
sierra-cli masternode status
```
***

## Usage:
```
sierra-cli mnsync status
sierra-cli getinfo
sierra-cli masternode status
```
Also, if you want to check/start/stop **Sierra** , run one of the following commands as **root**:

```
systemctl status Sierra #To check the service is running.
systemctl start Sierra #To start Sierra service.
systemctl stop Sierra #To stop Sierra service.
systemctl is-enabled Sierra #To check whetether Sierra service is enabled on boot or not.
```
***

## Masternode update:
In order to update your Sierra Masternode to version 2.0.0.0, please run the following commands:
```
cd /tmp
wget -N https://github.com/sierracoin-foundation/sierra/releases/download/v.2.0.0/daemon-linux2.0.0.zip
unzip -x daemon-linux2.0.0.zip
cd daemon
chmod +x *
systemctl stop Sierra
mv sierrad sierra-cli /usr/local/bin
systemctl start Sierra
cd /tmp
rm -r ./{daemon-linux2.0.0.zip,daemon}
sierra-cli getinfo
```
Open your desktop wallet and start the node from there.
***

## Donations:
Any donation is highly appreciated.

**BTC**: 3MQLEcHXVvxpmwbB811qiC1c6g21ZKa7Jh  
**ETH**: 0x26B9dDa0616FE0759273D651e77Fe7dd7751E01E  
**LTC**: LNZpK4rCd1JVSB3rGKTAnTkudV9So9zexB  

