# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting
```
NAME: SANTHOSH S
REG.NO: 212224100052
```
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
<img width="1719" height="893" alt="Screenshot From 2026-02-06 22-10-26" src="https://github.com/user-attachments/assets/165e5242-2680-4d63-b865-4bf978682483" />


Invoke msfconsole:
## OUTPUT:
<img width="1734" height="953" alt="Screenshot From 2026-02-06 22-11-13" src="https://github.com/user-attachments/assets/6faae846-bce2-49e8-90fb-073420e107ef" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
<img width="1734" height="953" alt="Screenshot From 2026-02-06 22-11-45" src="https://github.com/user-attachments/assets/605be1b8-8950-4655-a439-f3443fc73bdd" />




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="1292" height="1033" alt="Screenshot From 2026-02-06 22-15-37" src="https://github.com/user-attachments/assets/14c620d7-ff79-4127-8cf2-44b80c50432a" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="1489" height="1001" alt="Screenshot From 2026-02-06 22-25-27" src="https://github.com/user-attachments/assets/f8af6f58-6fff-48aa-a370-f6b75ff914f3" />



Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
<img width="1462" height="763" alt="Screenshot From 2026-02-06 22-27-45" src="https://github.com/user-attachments/assets/9d3c24c5-9a41-4f96-823e-c5bce1aecdad" />



Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:
<img width="1920" height="913" alt="Screenshot From 2026-02-06 22-29-49" src="https://github.com/user-attachments/assets/5c081062-4312-48e1-be65-283c4e0b3c55" />



The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init




## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="1907" height="411" alt="Screenshot From 2026-02-06 22-32-23" src="https://github.com/user-attachments/assets/6720d6d3-d17b-45ed-9347-41f23d8ca40f" />


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="1920" height="711" alt="Screenshot From 2026-02-06 22-32-53" src="https://github.com/user-attachments/assets/5fd0e91c-0242-4c2f-a310-23e3754600ef" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
<img width="1920" height="839" alt="Screenshot From 2026-02-06 22-33-49" src="https://github.com/user-attachments/assets/471715a1-5235-4f2e-83a8-0f8bc77a662b" />




Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:
<img width="1920" height="290" alt="Screenshot From 2026-02-06 22-34-29" src="https://github.com/user-attachments/assets/ebb46182-22b7-4251-8494-318272126b04" />



After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:
<img width="1920" height="622" alt="Screenshot From 2026-02-06 22-36-36" src="https://github.com/user-attachments/assets/16649f77-ad83-450a-bb9e-4d15756022bb" />






## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
