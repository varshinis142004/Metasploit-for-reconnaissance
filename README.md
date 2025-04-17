# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
Find out the ip address of the attackers system

## OUTPUT:
<img src="https://github.com/user-attachments/assets/e714b70b-b8cc-4b38-a2d8-bf41690ee1ec" width=600>


Invoke msfconsole:

## OUTPUT:
<img src="https://github.com/user-attachments/assets/184d5d2d-16ad-4ea5-adf8-f502fbb1f43d" width=600>


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:
<img src="https://github.com/user-attachments/assets/49c1d27c-ab36-4886-b13b-e3bb024f9787" width=600>


Perform Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000
## OUTPUT:
<img src="https://github.com/user-attachments/assets/3a90bf7b-9a3d-4976-b23a-b4e4d0a332f3" width=600>

use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img src="https://github.com/user-attachments/assets/3a90bf7b-9a3d-4976-b23a-b4e4d0a332f3" width=600>

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
<img src="https://github.com/user-attachments/assets/95817972-9f6a-4636-a877-2c7e9dd47387" width=600>

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:
<img src="https://github.com/user-attachments/assets/b24f06a4-5219-4d16-b603-e49b2398d3a5" width=600>


The info command provides information regarding a module or platform,
## OUTPUT:
<img src="https://github.com/user-attachments/assets/8f197eb6-7772-42e4-bcf7-161210a032ea" width=600>


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
## OUTPUT:
<img src="https://github.com/user-attachments/assets/05981134-5bae-4378-86cb-f4a5d5c1f179" width=600>


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img src="https://github.com/user-attachments/assets/9c2bcdb1-0b66-4266-87ad-b4df9c8ebc53" width=600>


use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
<img src="https://github.com/user-attachments/assets/2a8e3cb2-2ce5-4e50-aad2-f60a21425156" width=600>


Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:
<img src="https://github.com/user-attachments/assets/246cdc52-827a-4aab-9e28-08f38563e076" width=600>


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:
<img src="https://github.com/user-attachments/assets/dc78fba5-d114-4606-ba7d-b6c67aceb8fd" width=600>


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:
<img src="https://github.com/user-attachments/assets/0fad27f3-db13-440e-aea9-0898a1af60a9" width=600>
<img src="https://github.com/user-attachments/assets/4aafb69b-1087-42a1-b3f2-2528c2d79d83" width=600>





## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
