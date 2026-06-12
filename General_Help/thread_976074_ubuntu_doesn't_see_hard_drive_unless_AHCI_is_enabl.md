---
title: "ubuntu doesn't see hard drive unless AHCI is enabled"
date: 2008-11-09
forum: General Help
---

### Post by drumstyx on 2008-11-09
Hi there,
for some reason, ubuntu doesn't recognize that a hard disk even exists, so i can't install. if i enable ahci in the bios it'll work, but then windows won't work (i'm gonna dual boot). what's missing?

---

### Post by quibbler on 2008-11-09
I had a similar problem. What I did was:

set bios to ahci
at opening screen when installing press F6 (other options)
remove quiet splash and replace with "all_generic_ide" without quotes.
Install Ubuntu.
After install edit /boot/grub/menu.lst and add that to first option for Ubuntu
reboot and change bios to ide from ahci.

You should now be able to boot to both Ubuntu and windows.

Regards quibbler

---

