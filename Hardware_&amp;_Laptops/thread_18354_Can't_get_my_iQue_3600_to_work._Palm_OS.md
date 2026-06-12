---
title: "Can't get my iQue 3600 to work. Palm OS"
date: 2005-03-06
forum: Hardware &amp; Laptops
---

### Post by selinium on 2005-03-06
I am trying to get my iQue to connect to Ubuntu but I am having problems.
I have checked that gnome-pilot is correctly installed.

In device manager, during syncronisation the iQue grabs 2 serial connections via usb.
ttyUSB1 and ttyUSB2.

I know that the conduit supports the Ique.
Here is the lsusb report
[COLOR=Blue]
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 0403:fc82 Future Technology Devices International, Ltd
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 091e:0004 Garmin International  /* this is the iQue */
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000
[/COLOR]
I have USB1.1 and a USB 2.0 PCI card. Both of which are operational.

The only thing I don't appear to have is a /dev/pilot 

Any help gratefully received!

Cheers,

James Thomas

---

### Post by lurker on 2005-05-23
Try changing the Port setting to /dev/ttyUSB1 (the first port that the iQue grabs).  This  worked for me.

I tried creating a symbolic link for /def/pilot that pointed to the USB port, but the link would vanish after the after the ports were released.

---

