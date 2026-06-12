---
title: "MFC 240C install problem in jaunty"
date: 2009-04-25
forum: Hardware
---

### Post by Ruhani04 on 2009-04-25
I need some pointers where I can find the basic-permissions.rules in jaunty to get my scanner going with my brother MFC240c.
For 8.10 brother says:

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

Unfortunately this file doesn't exist in jaunty in the same place. I got the printer installed fine but the sanner shows an I/O fault with the current settings.

---

### Post by Ruhani04 on 2009-04-26
Problem solved.
=D>
In jaunty the rules are now in
lib\udev\rules.d

---

