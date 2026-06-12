---
title: "USB - detect inserted device problem"
date: 2013-02-23
forum: Hardware
---

### Post by danteX on 2013-02-23
Hi, I have a problem with detection of usb devices. 

The problem is that after I plug in a usb device like printer or flash disk or anything else, the device is not recolonized. Like if it where not plugged in. This problem began after I installed the new release of Ubuntu 12.10, the usb drivers in 12.04 worked fine. The interesting thing is that the inserted devices are recognized after restarting the computer at booting and then I can use them normally again.

My motherboard is M3A78-EMH HDMI.

this is the output of lsusb before inserting a usb device

dante@Ubuntu:/$ lsusb
Bus 001 Device 004: ID 046d:081d Logitech, Inc. HD Webcam C510
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


this is the output after inserting a printer and a flash disk

dante@Ubuntu:/$ lsusb
Bus 001 Device 004: ID 046d:081d Logitech, Inc. HD Webcam C510
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and this is the output after restarting the system

dante@Ubuntu:~$ lsusb
Bus 001 Device 004: ID 046d:081d Logitech, Inc. HD Webcam C510
Bus 002 Device 002: ID 03f0:4117 Hewlett-Packard LaserJet 1018
Bus 002 Device 003: ID 1005:b113 Apacer Technology, Inc. Handy Steno 2.0/HT203
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

as you can see the usb devices are recognized only after restart.

Has someone pleas any ides how to fix this problem. Thx

---

