---
title: "USB DVD drive driver problem"
date: 2012-12-19
forum: Hardware
---

### Post by matthewhenry on 2012-12-19
I have a Foxconn Nanosaur e350 nettop ([http://www.dinopc.com/shop/pc/NEW-Nanosaur-E350-124p1083.htm]("http://www.dinopc.com/shop/pc/NEW-Nanosaur-E350-124p1083.htm")) and I've a Samsung USB se-s084c CD/-DVD writer which isn't recognised. 
I'm running Ubuntu 12.04
Does anyone know how i can get it to work? Is it a problem with the driver?

Help! I'm a noob!

Thank you

---

### Post by cwsnyder on 2012-12-19
What is your terminal output when you type the command **lsusb** with the Samsung drive connected?  You shouldn't have any problems with a driver, if the drive works.

---

### Post by matthewhenry on 2012-12-20
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 0bc2:50a5 Seagate RSS LLC 
Bus 001 Device 004: ID 13fd:0842 Initio Corporation 
Bus 001 Device 005: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 006: ID 045e:0773 Microsoft Corp.

---

### Post by matthewhenry on 2012-12-20
Sorted out the problem... DVD DRive had packed up... so all sorted now :)

---

