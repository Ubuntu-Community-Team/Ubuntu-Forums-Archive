---
title: "GRUB installed on wrong hardisk?"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by Dr.Fuzzy on 2009-11-05
Hi to all,

i apologise if this question has already been answered. To cut a long story sort, I have two SATA drives in my PC (250 GB for OS and 500 GB for storage), the 1st one with Windows XP already installed and Ubuntu 9.10 which I've just installed side-by-side with XP for multi boot. Surprisingly, after installation and reboot, I realised that GRUB has been installed on the 2nd HD!. Now, if I boot from the 1st HD no GRUB menu appears and the PC freezes, whereas if I change the boot order on bios to boot from the 2nd HD, the menu appears and I can dual boot normally. Any ideas why did this happened in the first place and how can I fix it in order to boot from the primary HD (250GB, where Linux and XP are installed)?

sudo fdisk -l , and I get this:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32c2da86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20073   161236341    7  HPFS/NTFS
/dev/sdb2           20074       30515    83875365    5  Extended
/dev/sdb5           20074       30084    80413326   83  Linux
/dev/sdb6           30085       30515     3461976   82  Linux swap / Solaris
    

Thanx! ;)

---

### Post by Dr.Fuzzy on 2009-11-06
Anyone?

---

