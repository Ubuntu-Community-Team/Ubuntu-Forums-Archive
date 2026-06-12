---
title: "Newbie request for printer installation"
date: 2009-04-29
forum: Hardware
---

### Post by MichaelIan on 2009-04-29
Being a newcomer to Linux I installed UBUNTU 8.1 (Intrepid Ibex) as a dual boot system with Windows XP. 
I have a Canon iSensys LBP 3010 Laser Printer.  After finding a suitable pair of drivers from Canon for the Debian system I installed them as best I could but could not get the printer to work. 
I have now taken the opportunity to install Ubuntu Version 9.04 (Jaunty Jackalope) in the hope of finding that the new system had solved the problem but this has not happened.
When I look at System > Administration > Printing,  the Canon 3010 is shown as the default printer.  In the Printer Configuration > Printer State the 3010 is shown as "Idle - Printer is now on line".
When I try to print a document the Canon 3010 is shown as "Ready" and as the default printer.  On pressing Print nothing happens.
Going back to the System > Administration > Printing the 3010 is seen to be "Processing" but no printing occurs.
Any assistance would be gratefully received but being new to Linux I do need fairly comprehensive instruction to carry out any proposed alterations and or manipulations.  I would also appreciate any help and assistance in collecting suitable information in order to help the helpers.  I tried to use the Troubleshooter but the resulting file was very large and unfortunately meaningless to me.
MichaelIan

---

### Post by isparkes on 2009-06-27
Exactly the same symptoms.

9.04 Jaunty x64
Canon LBP 3010

---

### Post by eldarskiy on 2009-07-15
I have same problem. I used hundred topics and posts from many sites, but its all for 2900, not for 3010 , and its no one works for me.
But still no solution for 3010.....

---

### Post by eldarskiy on 2009-07-15
Actually printer market as ready, but all jobs in pending. Printer won't work
Drivers was downloaded from official site (version 1.8, 1.6, no mater).

---

### Post by rcasha on 2009-10-05
Same problem here. Any news on this issue?

---

### Post by frdrx on 2009-11-26
I have just successfully installed this printer with Ubuntu 9.10. by partly following [this how-to](http://petrdrhlik.webzdarma.cz/ict/pocitace/odstranovani-potizi/ubuntu/instalace-tiskarny-canon-lbp3010-v-ubuntu.htm) written by Petr Drhlík. The printer seems to be working perfectly. It was bloody complicated, however, and required me to install libstdc++5 from Jaunty, download the Canon CAPT Printer Driver for Linux and modify the cndrvcups-common_1.80-1_i386.deb package so that it would depend on libcups2 rather than libcupsys2. I also had to manually start the ccpd daemon and add it to the runlevels. Let me know if you want me to post detailed instructions.

---

### Post by MichaelIan on 2009-11-27
Thank you for this post, I was beginning to think that although Canon provide "a Linux driver" it was useless with Ubuntu.
I would greatly appreciate a complete description of the means to get my LBP3010 working with Ubuntu rather than having to use it only with Windows.
I still consider myself a very green user of Linux and would need very explicit instructions. The description in the last post is mostly well beyond my experience.

---

### Post by frdrx on 2009-11-27
> **MichaelIan said:**
> Thank you for this post, I was beginning to think that although Canon provide "a Linux driver" it was useless with Ubuntu.
I would greatly appreciate a complete description of the means to get my LBP3010 working with Ubuntu rather than having to use it only with Windows.
I still consider myself a very green user of Linux and would need very explicit instructions. The description in the last post is mostly well beyond my experience.

I'll get to it as soon as possible. Are you still on 8.10. or have you upgraded? Is your system 32- or 64-bit?

---

### Post by MichaelIan on 2009-12-02
First apologies for late reply, I have been away from home and my computer.
Thank you for offering to show how a Canon 3010 may be used with Ubuntu.
I have upgraded to Version 9.10 and am using a 32 bit system

---

### Post by frdrx on 2009-12-02
> **MichaelIan said:**
> First apologies for late reply, I have been away from home and my computer.
Thank you for offering to show how a Canon 3010 may be used with Ubuntu.
I have upgraded to Version 9.10 and am using a 32 bit system

Thanks. I didn't have enough time to write anything, but I will hopefully be able to post the instructions tomorrow.

---

### Post by notlistening on 2010-01-06
There is an easier guide in the Ubuntu Documentation that I wrote if your interested.

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/LBP3010](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/LBP3010)

---

### Post by notlistening on 2010-01-06
Double post ;)

---

### Post by MichaelIan on 2010-01-17
Thank you for directing me to the site describing the installation of the Canon drivers for the LBP 3010.

I regret to say that I am still having trouble.

I managed to get both parts of the Canon drivers installed after correcting the dependency problems. (Part 3 of instructions)
 
michael@Athlon:~$ sudo dpkg -l | grep cndrvcups

ii  cndrvcups-capt                                               1.80-1                                     Canon CAPT Printer Driver for Linux.

ii  cndrvcups-common                                             1.80-1                                     Canon Printer Driver Common Modules Ver.1.80


After replacing the script in the ccpd file and restarting it [OK] I could not make a test print and going forward from there I had trouble when trying to implement part   5.  Karmic Auto Start ccpd :

michael@Athlon:~$ sudo update-rc.d ccpd defaults 50

update-rc.d: warning: ccpd start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (2 3)

update-rc.d: warning: ccpd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 1 4 5 6)

 System start/stop links for /etc/init.d/ccpd already exist.


I have been around the installation procedure a few times and print queue indicates the test print instruction as No 70!

Checking the verification that all drivers are in place indicates that one is missing.:

michael@Athlon:~$ sudo /etc/init.d/ccpd status

Canon Printer Daemon for CUPS: ccpd: 1177



Any directions as to where I should try next would be very gratefully received.

---

### Post by MichaelIan on 2010-01-19
Further to my previous post I have now managed to get version 1.9 of the Canon drivers.  (1.8 is still the latest version shown on Canon UK Support)
Having been through the procedures again I now get a slightly different verification of the ccpd process:

Canon Printer Daemon for CUPS: ccpd: 1203

Still only one and no printing

---

