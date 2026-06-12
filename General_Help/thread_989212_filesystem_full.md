---
title: "filesystem full"
date: 2008-11-21
forum: General Help
---

### Post by cupevampe on 2008-11-21
hei everyone... im new to ubuntu and really like ti although with ups and downs... there are more ups than downs anyway

i like it so much my filesystem is now full, because i've installed to much stuff in wine i guess

is there any way to expand my filesystem with gparted?

My computer has a 120GB HD and has is a dualboot system with XP and Ubuntu 8.10... and too much free space on the winz partition.

any help as usual is highly appreciaed

---

### Post by taurus on 2008-11-21
Theoretically, you can boot your machine with the LiveCD.  Then, use gparted (System -> Administration) and shrink your windows partition and expand your Ubuntu partition to take up that space.  It depends on the layout of your harddrive though.  Again, before you shrink or expand anything, ALWAYS backup your personal files in case something goes wrong.

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by cupevampe on 2008-11-21
here it is

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c7087d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11966    96116863+   7  HPFS/NTFS
/dev/sda2           11967       14325    18948667+   f  W95 Ext'd (LBA)
/dev/sda3           14326       14593     2152710   82  Linux swap / Solaris
/dev/sda5           11967       13646    13494568+  83  Linux
/dev/sda6           13647       14325     5454036   83  Linux

Disk /dev/sdb: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe4a26b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7302    58652464+   b  W95 FAT32

---

### Post by taurus on 2008-11-21
It's going to be hard since your ntfs is a primary partition while your linux partitions are logical partitions.

---

