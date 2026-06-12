---
title: "[Solved] Module for AC'97 Modem Controller (rev a0)"
date: 2014-03-13
forum: Hardware
---

### Post by balubeto on 2014-03-13
Hi

I installed Lubuntu 13.10 32-bit on a notebook and, using the command **lspci -k**, the analog modem is detected in this way:

> 
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
 Subsystem: ASUSTeK Computer Inc. Device 1816


Someone could indicate what package I should install to make sure that Linux has the module suitable to handle it properly?

The problem is that I really have to use the analog modem since my home on vacation has only an analog connection. So, could you help me?

Thanks

Bye

---

### Post by phidia on 2014-03-13
You can give [this]("https://wiki.debian.org/slmodem") a read and see if you can get that modem working for you. If you do even have even partial success with that report back because there have been a number of people asking about dial up modems recently.

---

### Post by balubeto on 2014-03-14
In practice, the proper procedure to install the analog modem is:


1) sudo apt-get install sl-modem-daemon sl-modem-source


2) sudo depmod -a


3) sudo modprobe slamr


4) sudo /etc/init.d/sl-modem-daemon restart


5) sudo vwdialconf


Thanks


Bye

---

