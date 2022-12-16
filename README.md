## nxiq-token-manager

### Description

Create, delete and list Nexus IQ user tokens. 
This script also allows the user to find and delete 'expired' tokens.

&#9888; Nexus IQ does not currently provide any token expiry function.
An 'expired' token is simply a token older than a user-defined period of time at runtime of this script.

By default, the age of a token is set to one year.

### Prerequisites

Python 3.10+

### Defaults

- -u = admin (Nexus IQ user name)
- -p = admin123 (Nexus IQ user password)
- -s = http://localhost:8070 (Nexus IQ server url)
- -m = list (list all tokens) [listx|create|delete|delete_expired|notify]
- -r = Internal (IQ Authentication realm) [SAML|Crowd|<LDAP Server Id>]
- -a = 365 (age after which a token expires - days)
- -f = ./expire-tokens.json (listing 'expired' tokens with '-m listx' writes them to this file)

### Examples

#### List all tokens (with defaults)
```bash
python3 nxiq-token-manager
````
#### List all tokens that are 'expired' after 1 year old or older (with defaults). Writes the tokens from the file in -f
```bash
python3 nxiq-token-manager -m listx
```
#### List all tokens that are 'expired' after 30 days or older (with defaults). Writes the tokens from the file in -f
```bash
python3 nxiq-token-manager -m listx -a 30
```
#### List all tokens that are 'expired' after 1 year old or older for SAML users (with defaults). Writes the tokens from the file in -f
```bash
python3 nxiq-token-manager -m listx -r SAML
```
#### Remove 'expired' tokens (with defaults). Reads the tokens from the file in -f
```bash
python3 nxiq-token-manager -m delete_expired 
```
#### Create a token (with default admin user credentials and server)
```bash
python3 nxiq-token-manager -m create
```
#### Create a token for a local user
```bash
python3 nxiq-token-manager -m create -u sotudeko -p my password -s http://iqserver:8070
```
#### Create a token for a SAML user
```bash
python3 nxiq-token-manager -m create -u sotudeko -p my password -s http://iqserver:8070 -r SAML
```
#### Send notification email to owners of expiring tokens. Reads the tokens from the file in -f
```bash
python3 nxiq-token-manager -m notify 
```


### Disclaimer

The script in this repository is NOT SUPPORTED by Sonatype, and is a contribution of ours to the open source community (read: you!)

Don't worry, using this community item does not "void your warranty". In a worst case scenario, you may be asked by the Sonatype Support team to remove the community item in order to determine the root cause of any issues.

Please remember:

This purpose of this script to provide an example of using the API for automating managing Nexus IQ tokens.
Please take a copy and adapt for your own use cases.

Use this contribution at the risk tolerance that you have.

Do NOT file Sonatype support tickets related to this script

DO file issues here on GitHub, so that the community can pitch in




