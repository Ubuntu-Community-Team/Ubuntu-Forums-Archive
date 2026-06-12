---
title: "Scanner for MFC 240c install issues"
date: 2009-02-28
forum: Hardware
---

### Post by lbetts on 2009-02-28
Ok. I managed to get the printer working well.

Now I'm trying to get the scanner working. I downloaded the drivers from Brother to the desktop. Doubleclicked them and the ran their install.


The scanner shows installed in the packages manager.

When I open the Xsane program I get an error message 

Failed to open device 'brother2:bus2;dev2';
Error during device i/o

Did a search and ran the lsusb command and got the following

betts@betts-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 002: ID 04f9:01ab Brother Industries, Ltd MFC-240C
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
betts@betts-desktop:~$ 

Don't see the scanner.

What do I do?

System info
Acer Aspire AMD64
Ubuntu 8.10 64 bit

---

### Post by Ruhani04 on 2009-04-25
You need to do this according to brother:
Ubuntu 8.04/8.04.1, 8.10 
1. Open "/etc/udev/rules.d/40-basic-permissions.rules" file. 
2. Edit "0664" to "0666" in "USB devices" section. 
Before the edit--------------------------------- 
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device",                MODE="0664"
After the edit---------------------------------- 
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device",                MODE="0666"
3. Restart the OS. 

Hope that helps.8-)

PS: I just saw you have 64bit. There is some more stuff you need to do. Just go to the brother website and follow the additional instructions for 64bit systems.

---

### Post by Ruhani04 on 2009-04-25
One more place you can check in the forum:

[http://ubuntuforums.org/showthread.php?t=590793&highlight=mfc+240c](http://ubuntuforums.org/showthread.php?t=590793&highlight=mfc+240c)

---

