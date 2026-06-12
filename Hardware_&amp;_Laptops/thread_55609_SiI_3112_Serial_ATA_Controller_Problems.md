---
title: "SiI 3112 Serial ATA Controller Problems"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by kristian on 2005-08-09
I have a problem that the harddrives that is attached to my serial ata controller don't get mounted under boot as they should acording to my fstab. All other partitions on harddrives that's not SATA interfaced get's mounted properly. However if I mount them manualy after bootup there is no problem at all. (SATA driver is compiled into the kernel)...

from fstab:
/dev/hda1       /mnt/hda1      ntfs    defaults         0       0 | works
/dev/sda1       /mnt/sda1       ext2    defaults        0       0 | no
/dev/sdb1       /mnt/sdb1       ext3    defaults        0       0 | and no

uname -a:
Linux gir 2.6.12.4 #1 Sat Aug 6 13:35:26 CEST 2005 i686 GNU/Linux

---

