---
title: "Can't setup my new HP Color Laserjet Pro MFP M277DW"
date: 2015-08-22
forum: Hardware
---

### Post by RaZoR1394 on 2015-08-22
I got a new printer, the HP Color Laserjet Pro MFP M277DW. It works in windows without any major hitches but in Ubuntu, I cannot even install it. I use Ubuntu 15.04 amd64 with the latest updates.

There is a page on the printer:

[http://hplipopensource.com/hplip-web/models/color_laserjet/hp_color_laserjet_mfp_m277dw.html](http://hplipopensource.com/hplip-web/models/color_laserjet/hp_color_laserjet_mfp_m277dw.html)

When I run hp-setup as descriped on that page I get this:

```
flamingeyes@zeus:~$ hp-setup 

HP Linux Imaging and Printing System (ver. 3.15.2)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-15 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb
Searching... (bus=net, timeout=5, ttl=4, search=(None) desc=0, method=slp)
error: No devices found on bus: net

```

Running hp-setup as root doesn't help either.

lsusb seems to find it.

```

flamingeyes@zeus:~$ lsusb
Bus 008 Device 004: ID 14cd:8168 Super Top 
Bus 008 Device 003: ID 048d:1336 Integrated Technology Express, Inc. SD/MMC Cardreader
Bus 008 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 008: ID 2109:0810  
Bus 007 Device 007: ID 2109:0810  
Bus 007 Device 005: ID 1b1c:1b11 Corsair 
Bus 007 Device 004: ID 1b1c:1b12 Corsair 
Bus 007 Device 009: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 007 Device 006: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
Bus 007 Device 010: ID 03f0:3b2a Hewlett-Packard 
Bus 007 Device 003: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
Bus 007 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 2109:0810  
Bus 002 Device 002: ID 2109:0810  
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I can reach the printers web interface from Chrome by typing the ip adress of the printer in the adress box.

---

### Post by RaZoR1394 on 2015-08-23
I didn't fully read the requirements for installing this printer. The hplip provided with Ubuntu 15.04 was too old. I downloaded and ran the latest hplip installer from sourceforge. After installing hplip I added the printer just like usual. The printer and scanner seems to work now.

---

### Post by luke-jr on 2015-09-29
Did you need the proprietary plugin for it to work, or was it fine with just free software?

---

### Post by hanasaki on 2015-10-11
using 3.15.9 install went fine however configuring through hp-setup results in no PPD found and the below on the console:
Also, any idea what needs to be restarted from the console to avoid needed a reboot?  hp-setup did not find the printer automatically until rebooting.  tried restarting cups and cups-browsed

[FONT=courier new][COLOR=#FF0000]error: No PPD found for model color_laserjet_pro_mfp_m277 using old algorithm.
error: No appropriate print PPD file found for model hp_color_laserjet_mfp_m277dw
error: Unable To read the XML data from device
error: Unable To read the XML data from device[/COLOR][/FONT]

---

