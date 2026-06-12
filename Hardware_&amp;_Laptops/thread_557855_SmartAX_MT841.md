---
title: "SmartAX MT841"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by sulekha on 2007-09-23
Hi all,

1)

I am using a SmartAX MT841 ADSL router to connect to internet.
then i happened to read the following article:-
[http://www.indiabroadband.net/bsnl-broadband/2669-problem-modem-router-mt841.html](http://www.indiabroadband.net/bsnl-broadband/2669-problem-modem-router-mt841.html)

on the above link the procedure for taking firmware backup is given as

on windows XP , you may try to take a backup of
current firmware by using the following command :
tftp -i 192.168.1.1 GET c:\MT841teimage.bin

now my question is what is the equivalent in ubuntu dapper ???

I installed tftp via synaptic and tried the following:-

tftp -i 192.168.1.1 GET ~/Desktop/ MT841teimage.bin

then i got the message as usage: tftp host-name [port]
so what will be the command/procedure to make a back up of MT841 firmware???

2)The firmware for MT841, which i have is V100R001C01B021SP01 dated July 19 2005.
I believe there is latest firmware for this model of modem.
Where can i get the latest firmware ???
what are the steps for upgrading the firmware???
In case my modem stops working after upgrade what should i do to undo the upgrade??
What are the precautionary measures ??

---

### Post by asvravi on 2008-01-20
The tftp in ubuntu is interactive and does not take command line arguments except for hostname and port. So type in "tftp 192.168.1.1" and issue the rest of the commands at the tftp shell which opens.
eg;

> tftp 192.168.1.1

tftp> bin
tftp> get MT841teimage.bin

.

---

