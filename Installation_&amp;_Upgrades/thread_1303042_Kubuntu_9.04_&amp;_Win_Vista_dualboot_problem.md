---
title: "Kubuntu 9.04 &amp; Win Vista dualboot problem"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by calin.burloiu on 2009-10-27
I have 2 partitions on a hard-disk, a NTFS for Windows Vista and an EXT3 for Kubuntu (plus a SWAP one). I tried to reinstall Linux by using a Kubuntu 9.04 installation CD. I chose "Specify partitions manually" in order to install the Linux on the EXT3 partition as the old one. I also checked the format option and chose "/" as the root mounting point.
After installation I saw that I can't boot Kubuntu, because instead of Grub Windows is booting.
I used the live CD to enter in the EXT3 partition and it seems that Kubuntu and Grub has been installed there. I copied the menu.lst from this partition and use it in NeoGrub with EasyBCD but it still doesn't work.

---

### Post by calin.burloiu on 2009-10-27
I resolved the problem by reading another post. Thank you! Great forum!

---

