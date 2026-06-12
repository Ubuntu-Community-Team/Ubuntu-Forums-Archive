---
title: "Dual boot Problem??"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by buzov007 on 2009-02-18
I have ubunut and xp,everything was working ok ,until i used particion magic.

Now on this command gksudo gedit /boot/grub/menu.lst says:
NOTHING
Empty File

My hard disk are: fdisk -l

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9729    57665317+   f  W95 Ext'd (LBA)
/dev/sda5            2551        7966    43503988+   7  HPFS/NTFS
/dev/sda6            7967        7991      200781    7  HPFS/NTFS
/dev/sda7            7992        8016      200781    7  HPFS/NTFS
/dev/sda8            8017        8925     7301511    7  HPFS/NTFS
/dev/sda9   *        8926        9688     6128766   83  Linux
/dev/sda10           9689        9729      329301   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fce4c49

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS


Please Help!!

---

### Post by mozkill on 2009-02-18
you should have backed it up with CloneZilla  before you did the partition magic.   maybe someone else can help you with your predicament.

---

