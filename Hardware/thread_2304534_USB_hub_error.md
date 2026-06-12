---
title: "USB hub error"
date: 2015-11-27
forum: Hardware
---

### Post by Evil Wayz on 2015-11-27
When I turn on my computer, instead of getting a ubuntu loading screen, I get a long string of actions and whther they were ok or failed.  I have a powered ten slot usb hub, and teh computer insists that they fail.  But the thing still works.  Only certain devices that can charge and act as mass storage ( phone, mp3 player, GPS, etc) only charge.  And when I attach portable hard drives they read fine but when i copy or move stuff from them they are slow as lolasses.  Is there a driver or a tweak I can use to force ubuntu to recognize my hub properly?

---

### Post by Evil Wayz on 2015-11-30
This is hte output for lsusb, which doesn't make sense, i have two external usb ports on the front of my box, one is connected to an external hard drive, and the other is connected to a ten slt powered USB hub.  There shouldn't be any usb 1.0 devices. But there they are.  

[HTML]Bus 001 Device 008: ID 1058:0748 Western Digital Technologies, Inc. My Passport (WDBKXH, WDBY8L)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 010: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 005 Device 006: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 005: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 003: ID 1997:0409  
Bus 005 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1ea7:0011  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 045e:0752 Microsoft Corp. Wired Keyboard 400
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/HTML]

---

