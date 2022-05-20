# Template OPNSense FW Availability Checks

Perform Website/DNS Server Availability Checks via Zabbix Active Agent on OPNSense.

All Checks are performed direclty from the OPNSense, the results are transfered to the Zabbix Server.

The Template used two examples for the Checks: GoogleDNS and a fictive ExternalDB

## Installation

1. Import the Template

2. Edit or Add all required Sites/Server. Start by creating the item, then add a trigger

3. Optional add an Web scenario to perform HTTP-Statuscode 200 requests

4. Open your OPNSense WebUI, go to your Services>Zabbi Agent Section and click on Zabbix Features:

Check `Enable Active Checks`, add the Active Check Server or Proxy and optional PSK Encryption.

Open the Advanced Tab and add new user Parameters for each Sites/Server you want to check.

Example for GoogleDNS:

```
Enabled [x]
Key: pingtime.googledns
Command: ping -c 1 google.com | awk 'BEGIN {FS="[=]|[ ]"} {print $10}' | grep -v -e '^$'  | bc -l
Accept Parameters: [ ]
```
Just edit the adress for each Sites/Service, DNS or IPv4 addresses are required.
