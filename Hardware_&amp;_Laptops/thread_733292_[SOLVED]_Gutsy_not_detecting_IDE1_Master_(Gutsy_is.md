---
title: "[SOLVED] Gutsy not detecting IDE1 Master (Gutsy is installed on slave)"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by Barrucadu on 2008-03-23
I've just installed Gutsy on my brothers computer, on the IDE1 Slave, as neither the installer nor Gutsy detect it. It's not in /dev, and fdisk -l isn't finding anything either. What could be the problem?
The weird thing is that the installer detected Windows XP on the drive and added it to the GRUB list, but could not partition or mount it.

---

### Post by Barrucadu on 2008-03-23
I've just found that it is finding the IDE1 master - it is recognising it as /dev/hdb1, rather than /dev/hda1. Ubuntu seems to be treating the two harddrives as one for some reason.

---

