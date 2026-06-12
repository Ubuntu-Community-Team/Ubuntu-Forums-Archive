---
title: "Marvell Yukon Ethernet Controller in Ubuntu"
date: 2008-08-10
forum: Hardware
---

### Post by alebu on 2008-08-10
The same question was already asked here [http://ubuntuforums.org/showthread.php?t=369475](http://ubuntuforums.org/showthread.php?t=369475) but problem still exists. Have install_v10.60.2.3.tar.bz2 driver archive. Doing everything by READMY install.sh throws an error:
./functions: 44: Syntax error: "(" unexpected

Tried with kernel 2.6.24-19 and 2.6.26. Result is the same.

---

### Post by torsque on 2008-08-14
Hi ,

I have same problem... any solution ??

---

### Post by Daelyn on 2008-08-14
Strange that you guys have problems with that NIC.

I have a Marvel Yukon on my Sony VAIO laptop. It has always been automatically recognized and I have been using it flawless since Feisty.

Run:
```
 lspci 
```
and output the string containing the details of the controller. 

Can be different versions of the NIC that causes it maybe?

---

### Post by Der_Idiot on 2008-08-15
I have a Gateway P-7811 and it has a Marvel Yukon 88E8057 gigabit PCI-E port, and it was not recognized. I share your pain.

Ideas?

---

### Post by alebu on 2008-08-19
> **Daelyn said:**
> Strange that you guys have problems with that NIC.

I have a Marvel Yukon on my Sony VAIO laptop. It has always been automatically recognized and I have been using it flawless since Feisty.

Run:
```
 lspci 
```
and output the string containing the details of the controller. 

Can be different versions of the NIC that causes it maybe?

Listing of my lspci is available as attachment in thread [http://ubuntuforums.org/showthread.php?t=854355](http://ubuntuforums.org/showthread.php?t=854355)

---

### Post by torsque on 2008-08-20
Okay i accept it's not installing automaticly so how can i install it manually ?

---

### Post by alebu on 2008-08-22
Today I found that Marvell also has spacial driver for Linux 2.6 - Fedora. File is tar-bz2 archive. Maybe it is possible to convert it into appropriate Ubuntu package? Don't know how to do it?
Link on driver download: [http://www.marvell.com/drivers/driverDisplay.do?driverId=153](http://www.marvell.com/drivers/driverDisplay.do?driverId=153) .
Also some other link was in search results:[http://www.marvell.com/drivers/driverDisplay.do?driverId=203](http://www.marvell.com/drivers/driverDisplay.do?driverId=203)

---

### Post by Der_Idiot on 2008-08-25
Good idea, I'll try that myself and see if I can't get something from it. New chipsets are always fun, aren't they? :confused:

---

### Post by jurajpaulo on 2009-04-09
solution to "72: Syntax error: "(" unexpected":
replace "#!/bin/sh" with "#!/bin/bash" at the first line of install.sh

---

### Post by nikR on 2010-09-06
I've the same problem here.

---

### Post by mathia on 2010-09-17
Hi,

**[B]Installing Marvell Yukon driver on Ubuntu**, e.g. 8057:[/B]

Please install the following driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8057 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

and let me know if it works.

Have a lot of fun ...:razz:

---

### Post by foresto on 2011-10-26
> **alebu said:**
> Today I found that Marvell also has spacial driver for Linux 2.6 - Fedora. File is tar-bz2 archive. Maybe it is possible to convert it into appropriate Ubuntu package? Don't know how to do it?

I've done it.  See my announcement here:

[http://ubuntuforums.org/showthread.php?p=11382042#post11382042](http://ubuntuforums.org/showthread.php?p=11382042#post11382042)

---

### Post by FizzerJE on 2011-11-12
> **jurajpaulo said:**
> replace "#!/bin/sh" with "#!/bin/bash" at the first line of install.sh

Thanks Man...   Worked!!

---

### Post by mathia on 2011-11-15
I'm glad it has worked with your system.

I found the following statement in README
12  Troubleshooting
=================== 
Problem:  After running the "install.sh" script the error message 
          './functions: 44: Syntax error: "(" unexpected' is displayed.
Reason:   Your Linux sytem uses a Debian Almquist shell (dash) which is a Unix 
          shell and much smaller than bash but still aiming at POSIX-compliancy. 
        It requires less disk space but is also less feature-rich.
Solution: Use the following command: 'sudo bash ./install.sh'.

---

