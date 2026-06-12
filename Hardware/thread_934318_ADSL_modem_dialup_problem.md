---
title: "ADSL modem dialup problem"
date: 2008-09-30
forum: Hardware
---

### Post by esmailgad on 2008-09-30
Hi everyone
I have a D-link-210 ADSL modem connected to the computer HPDX2000 through USB and I have been trying to figure out how I can connect internet under ubuntu. using the command dmesg I got the following:
[   54.342704] ATM dev 0: ADSL state: stopped 
[   54.342709] ATM dev 0: ADSL line: down 

[   54.342704] ATM dev 0: ADSL state: stopped 
[   54.342709] ATM dev 0: ADSL line: down 

[   55.745941] ATM dev 0: ADSL state: running 


[   61.739224] ATM dev 0: ADSL line: attempting to activate 
[   61.950328] audit(1222788610.610:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4846 profile="/usr/sbin/cupsd" namespace="default" 
[   62.727555] ATM dev 0: ADSL line: down 


[   64.735347] ATM dev 0: ADSL line: attempting to activate 
[   65.724411] ATM dev 0: ADSL line: down 
[   67.732481] ATM dev 0: ADSL line: attempting to activate 
[   70.713645] ATM dev 0: ADSL line: training 
[   72.722715] ATM dev 0: ADSL line: channel analysis 
[   76.713902] ATM dev 0: ADSL line: exchange 
[   77.710952] ATM dev 0: ADSL line: up (288 kb/s down | 288 kb/s up) 
[   90.761861] NET: Registered protocol family 10 
[   90.762363] lo: Disabled Privacy Extensions 
[   90.762979] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   98.024939] UDF-fs: No VRS found 
[   98.070682] ISO 9660 Extensions: Microsoft Joliet Level 3 
[   98.071407] ISOFS: changing to secondary root 


I am new with ubuntu and linux as general, but I believe from these lines that the modem is detected and the ADSL line is working. the problem is that under network settings I can submit my username and password but the swettings give me one choice of modem connected through eth0. Also my connection type is pppoA and the settings give me only pppoE
So the question is how can I make my modem dial up the connection

---

