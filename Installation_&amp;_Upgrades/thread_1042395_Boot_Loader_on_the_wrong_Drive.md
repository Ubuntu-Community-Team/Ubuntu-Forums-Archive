---
title: "Boot Loader on the wrong Drive"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by Raymond_N on 2009-01-17
I have two hard-drives 1 is connected through the IDE and the other is connected through SATA.  The SATA drive is partitioned into two NTFS drives, this hard-drive is used for only my data and media files.  I installed XP on the IDE drive and told it to use half the drive.  When installing Ubuntu I used the rest of the IDE drive for Linux partitions.  The Ubuntu installer installed GRUB on the SATA drive and XP installed it's boot loader in the IDE drive.  The problem I have is my SATA controller on my motherboard doesn't always work when I boot up the computer so it would launch the XP boot loader.  The BIOS would automatically select the hard-drive with a boot loader when it loads.  To get into Ubunutu i would have to wait till the SATA controller wakes up then set my BIOS to boot from the SATA drive.  How can I Move GRUB on to the IDE Partition or put a boot loader on the IDE Partition to load Ubuntu.

---

### Post by logos34 on 2009-01-17
easiest way:

temporarily disconnect sata, reboot into the live cd desktop and reinstall Grub to the MBR of the IDE (see link my signture).  Reconnect the sata but afterward make sure the ide is set first in the Bios hard disk boot priority.

Good luck

---

