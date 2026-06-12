---
title: "Phone plugged into usb not recognized after upgrade to Intrepid"
date: 2009-04-05
forum: Hardware
---

### Post by rgl2020 on 2009-04-05
I upgraded from Hardy to Intrepid 2 days ago and have had a bunch of bugs that are slowly getting resolved.  This is the most problems I've had with an upgrade. *rant over*

I have a Samsung Blackjack phone that I sync in XP running inside Vbox.  There was no problems with Hardy.  After the upgrade to Intrepid, the USB device isn't recognized in Vbox.  I thought it was a Vbox problem, but it's recognizing my printer and other USB storage devices.  After reading through multiple posts, I can't figure out the problem.  There is no recognition of the device with lsusb.  The ouput of dmesg is:


[ 1004.160231] usb 1-2.3: new full speed USB device using ehci_hcd and address 6
[ 1019.232524] usb 1-2.3: device descriptor read/64, error -110
[ 1034.408818] usb 1-2.3: device descriptor read/64, error -110
[ 1034.584821] usb 1-2.3: new full speed USB device using ehci_hcd and address 7
[ 1049.657114] usb 1-2.3: device descriptor read/64, error -110
[ 1064.832406] usb 1-2.3: device descriptor read/64, error -110
[ 1065.008409] usb 1-2.3: new full speed USB device using ehci_hcd and address 8
[ 1070.028133] usb 1-2.3: device descriptor read/8, error -110
[ 1075.148106] usb 1-2.3: device descriptor read/8, error -110
[ 1075.324610] usb 1-2.3: new full speed USB device using ehci_hcd and address 9
[ 1080.344081] usb 1-2.3: device descriptor read/8, error -110
[ 1085.464056] usb 1-2.3: device descriptor read/8, error -110
[ 1085.568061] hub 1-2:1.0: unable to enumerate USB device on port 3


I'm stuck.  Any help or suggestions would be appreciated.

---

