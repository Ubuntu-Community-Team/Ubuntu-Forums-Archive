---
title: "HP Laserjet 1020 plus on Kubuntu 15.04 - error &quot;on hold&quot;"
date: 2015-09-16
forum: Hardware
---

### Post by neogarfield on 2015-09-16
**This is not an issue anymore since the printer is working for now, will remove this message and add info if I have further issues. Thank you.**

Hello,

I'm having trouble installing an HP Laserjet 1020 Plus printer on a desktop running Kubuntu 15.04. There are several kinds of errors that I'm getting.

1. Sometimes, the printer is not detected at all (not listed on lsusb). Sometimes it's detected on lsusb, but I receive the message that there are no printers connected when I try to install the printer via the CUPS web interface, hp-setup, and the Kubuntu printer settings window.

2. When it's detected and installed, sometimes I'm able to print, but most times, it does not print. The printer queue shows "On hold". Hitting retry via the kubuntu queue window, or "release" via the CUPS web interface does not help - it returns to the "On hold" status. And I'm not sure if it's an error, but the CUPS web interface shows the user as "Withheld".

These errors, mostly the second, persist, and I've tried the following-

1. Install the easiest way, via the Kubuntu printer settings window, selected the foo2zjs driver. Couldn't print. Removed the printer. Installed the printer the same way, but selecting the HP proprietary driver. Couldn't print. Deleted the printer.
2. Installed using hp-setup. Got one print, but after that the "On hold" occurs and doesn't go any further. Tried the usual cancel jobs, unplug, turn off, restart, replug etc. No change, all prints I give are kept "on hold".
3. Deleted the printer, ran hp-check and hp-doctor. Installed again using hp-setup. Didn't work. But, hp-check mentioned a couple of optional dependencies which I installed.
4. Deleted the printer. Completely removed HPLIP, CUPS, reinstalled. Then tried installing via hp-setup, Kubuntu printer settings, and CUPS web interface. Got a print again once, but after that the "on hold" kicked in.
5. Removed HPLIP and installed the foo2zjs printer driver. This did not get me a print out.

Finally, I deleted the foo2zjs driver, ran hp-check again, and installed the printer via hp-setup; again got a few print, and then went into "on hold".

I'm not very sure of what logs to get and post, so could you help me out with that? Any help to figure this out much appreciated! Trying to set this printer up for my professor.

EDIT: This is what hp-doctor now gives me
----------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_1020?serial=S4260EG
PPD: /etc/cups/ppd/HP_LaserJet_1020.ppd
PPD Description: HP LaserJet 1020, hpcups 3.15.2, requires proprietary plugin
Printer Rendering completedLaserJet_1020 is idle.  enabled since Wednesday 16 September 2015 05:03:46 PM IST
Required plug-in status: Installed
[B]error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_1020?serial=S4260EG
error: Device not found
error: Communication status: Failed

--------------
| PERMISSION |
--------------

 

Checking Permissions....
Permissions are correct.


Checking for Configured Queues....
 
Queue(s) configured correctly using HPLIP.


Checking for HP Properitery Plugin's....
Plugin's already installed
 

Checking for Printer Status....
error: 'HP_LaserJet_1020' Printer is either Powered-OFF or Failed to communicate.
[/B]
The printer is on, and connected. But, lsusb does not recognise it-

Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

UPDATE 2: Restarted, replugged, lsusb recognised the printer, and it's printing now. No errors shown in hp-doctor. Sorry for bothering anyone who went through this post. If the error recurs, will post. Thank you!

---

