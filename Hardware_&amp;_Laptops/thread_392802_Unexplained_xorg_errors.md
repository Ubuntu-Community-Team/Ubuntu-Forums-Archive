---
title: "Unexplained xorg errors"
date: 2007-03-24
forum: Hardware &amp; Laptops
---

### Post by benthegreat1 on 2007-03-24
Hello all fellow ubuntuers,
Ive been having fun installing all my ati drivers and stuff the last few weeks and thought I had it all sorted, untill i tried to install cedega, it fails all the graphics tests, and wont install any games.
Anyway when i check for errors in my xorg log the following comes up.
I dont care to much about cedega, but I cant rest while my system has errors.
I also cant run the fglrx control panel.

ben@matrix:~$ grep '^(EE)\|^(WW)' /var/log/Xorg.0.log
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

ben@matrix:~$ fireglcontrol
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: sequence lost (0x10001 > 0xa) in reply type 0x18!

Thanks in advance

---

### Post by benthegreat1 on 2007-04-12
Yep, all fixed
Ive installed the latest drivers from the ati site following the BinaryDriverHowto, and i now have no problems at all

---

