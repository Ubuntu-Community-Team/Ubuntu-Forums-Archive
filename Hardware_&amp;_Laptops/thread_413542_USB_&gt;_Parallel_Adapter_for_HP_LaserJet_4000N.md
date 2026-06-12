---
title: "USB &gt; Parallel Adapter for HP LaserJet 4000N"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by diceratops on 2007-04-19
I have an HP LaserJet 4000N printer that I'd like to get working with my Edgy installation. My new computer does not have a parallel port, so I purchased a USB > IEEE 1284 parallel adapter cable. However, I am not able to detect and install the printer correctly using the Gnome CUPS manager. No printers are detected, and the only printer port that is listed is "hp no_device_found." I have started and restarted the computer with various combinations of the cable plugged and unplugged.

When I run lsusb, I get the following output:

Bus 004 Device 005: ID 9948:5523  
Bus 004 Device 002: ID 056a:0010 Wacom Co., Ltd Graphire
Bus 004 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 413c:2005 Dell Computer Corp. 
Bus 006 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

By plugging and unplugging the adapter, I have determined that it is the one listed as "Bus 004 Device 005: ID 9948:5523."

So, is there some command or setting that I can use to print to this device, or add this device to the list of printer ports, using these settings? Or am I just out of luck?

Thanks!

Andy

---

