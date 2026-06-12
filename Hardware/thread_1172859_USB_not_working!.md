---
title: "USB not working!"
date: 2009-05-29
forum: Hardware
---

### Post by soliddiesel on 2009-05-29
I just installed Ubuntu Jaunty Jackalope, but i cant use any USB device, not my USB Modem, nor my USB mem.Stick! what is the problem!
Ubuntu is not plug and play? or is it something with my OS, by the way all hardware has been tested on windows, so there is no problem with it.

---

### Post by lisati on 2009-05-29
Some information about the kind of computer you're using might be helpful.......

---

### Post by mariliasaca on 2009-05-29
I have a similar problem. If my usb devices (mouse, printer, mem stick, usb modem) are plugged when I boot, it works OK. Otherwise I have to wait 15 minutes for the mouse to work. The memory stick just keep the name of the first one plugged, but I can access it (if any memory stick was plugged at the boot). 
I used 8.10 in this computer, no problems, and upgraded it. 
I have a Dell notebook.
Using the lspci I have (excluding the lines not related)
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


lsusb
Bus 002 Device 006: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 002 Device 005: ID 05a9:7670 OmniVision Technologies, Inc. OV7670 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 15d9:0a33 Unknown 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by soliddiesel on 2009-05-29
This is an AMD Athlon, 64 bit 3200+ on Asus ( A8V-VM SE) board, with 512 Mb Ram, built in LAN Sound VGA.

---

### Post by soliddiesel on 2009-06-04
Ok the USB started working, thanks to people who made Ubuntu, but since i ran some commands to see the actual position, so it turns out! the plug n  play function of Ubuntu for USB, that is the USB does get mounted but after a min or 2, when it has been pluged in, so ofcourse first reaction is!! its not working, so it does gets auto mounted, but in those 2 mins, i cant even see it in the list of USB devices, and nor disks connected.
but after 2 min when Ubuntu starts accessing it, i can see USB drive in drive list also
and ofcourse it is on the desktop.
Can any one explain what is happening!
Why it gets mounted so late!

---

