---
title: "Pressing ALT key During Boot"
date: 2008-08-19
forum: General Help
---

### Post by philgenius on 2008-08-19
Hi, all.

I have a Thinkpad T60 connected to an external USB Hard Drive with Ubuntu on it. Is it possible to configure the BIOS or something so that the second hard drive is booted when a certain key is pressed?

Another option would be to use boot.ini. But when I transfer over the files using dd to linux.bin and bring it to C:\ and edit boot.ini, it freezes upon booting linux. It displays "GRUB" and hangs. The /boot partition is within the first 1024 cylinders of the external USB HDD. What went wrong?

BTW, right now I use the SUPERGRUB disk to boot Ubuntu. Otherwise it loads the boot.ini menu.

---

### Post by philgenius on 2008-08-19
OK, now I just used the SuperGrubDisk and chose the option "Windows Chainloads Grub!". Now my computer hangs on boot with no text whatsoever. To see if any of you can solve this, I took a picture of the output of choosing to have windows chainload.

Photo of the Output of "Windows Chainloads GRUB!":

---

