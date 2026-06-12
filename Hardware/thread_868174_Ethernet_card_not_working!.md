---
title: "Ethernet card not working!"
date: 2008-07-23
forum: Hardware
---

### Post by ionreflex on 2008-07-23
Hey all,

I've decided to create another thread, but my problem is pratically the same as [Velvet Ghost]("http://ubuntuforums.org/showthread.php?t=862308"); but since I'm trying to install Xubuntu and that the NIC is not the same, I thought it would be a good idea not to mix the 2!

So I've just installed latest Xubuntu and it won't see the onboard NIC; deck is Compaq Evo N620c, NIC is "Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet" as detected by lspci.

Also, at first I tried installing driver from source downloaded from Broadcom support, but to no avail; anyway, the driver available seems older than the one already included (v3.86 vs. v3.85l).

2 things worth mentionning I came across in syslog and messages :

  tg3.c:v3.86 (November 9, 2007)
  tg3 : probe of 0000:02:0e.0 failed with error -22

Finally, I'll attach a .zip with logs for lspci, lsmod and dmesg.

Tankiou everyone!

PS : I know the NIC works because I've installed WindeXP on another HD!

---

### Post by ionreflex on 2008-07-24
Just to add, in my research I downloaded Broadcom Diag 11.05, burned and run it! Here'S the result :

> 
C Brd   Rv Bus     PCI Spd Base Irq NVM(avl/max) MAC Boot Code Config
0 5705M:A1 02:0E:0  32  33 9000  11     64k/ 64k Invalid serial NVRAM format

Checking IRQ : passed
Checking NVRAM Content : Failed

Failed! Error detected at device 0 (PCI slot 02:0E:0)
OS: DOS
Source: B57DIAG
Revision: 11.05
Unit Under Test: NIC
Module: EEPROM content test
Test Name: EEPROM Content Check
Error #: 67
Time Stamp: Web Jul 23 21:02:30 2008
Msg: Invalid Magic Value


Anybody ?

---

### Post by ionreflex on 2008-07-24
Damn! Also tried this to no avail... but I have a Xircom PCMCIA card inside, labeled eth0, so I tried installing the Broadcom NIC as bge0 instead... since it's a fresh, might as well reinstall it from scratch, if nobody can help me... :(

](*,)

---

### Post by ionreflex on 2008-07-29
Well, I guess not so trivial hey ? ;)

I've sumitted the bug to Broadcom support, I'll keep everyone posted...

---

### Post by ionreflex on 2008-08-13
> **ionreflex said:**
> Just to add, in my research I downloaded Broadcom Diag 11.05, burned and run it! Here'S the result :

... Msg: Invalid Magic Value ...

Anybody ?

Anybody has a N620c with working Ubuntu ? :confused:

---

