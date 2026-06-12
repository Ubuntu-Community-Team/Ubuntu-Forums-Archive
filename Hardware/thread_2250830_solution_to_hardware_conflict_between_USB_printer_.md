---
title: "solution to hardware conflict between USB printer &amp; scanner"
date: 2014-10-31
forum: Hardware
---

### Post by joverstreet1 on 2014-10-31
I have a USB Epson perfection 3490 photo scanner and a USB HP laserjet model 1020 printer.

There appears to be a conflict between these 2 USB devices.

When the printer is connected to a USB port, then the scanner will not function, it will work fine as long as the printer is not connected.

When the scanner is connected to a USB port, then the printer will not function, it will work fine as long as the scanner is not connected.

Below are the results of lsusb when both devices are connected.  I do not see any conflict here, do you ?  So, what is the problem.

Is there any way to resolve this conflict other than getting either a new printer or a new scanner ?

[B]Bus 001 Device 005: ID 03f0:2b17 Hewlett-Packard LaserJet 1020
Bus 001 Device 006: ID 04b8:0122 Seiko Epson Corp. GT-F520/GT-F570 [Perfection 3590 PHOTO]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/B]

Thanks.

---

