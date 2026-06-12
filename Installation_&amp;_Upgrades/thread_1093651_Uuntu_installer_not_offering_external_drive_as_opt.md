---
title: "Uuntu installer not offering external drive as option."
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by XSoph on 2009-03-11
Hey guys. So, I can boot Ubuntu on my HP 8530w from the live CD.
Gparted accurately recognizes my eSATA drive and all its volumes.
The Ubuntu installer will only read my internal notebook drive.
Even when I select the manual install option, it only picks up the internal drive.

I've made an ext3 partition, and unallocated, and an ntfs using gparted, and the installer still doesn't recognize any of them.

Got any ideas?

Thanks.

---

### Post by taurus on 2009-03-11
From Ubuntu LiveCD, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by XSoph on 2009-03-11
Wow! Quick reply. I'll go try it after class. Thanks.

---

### Post by XSoph on 2009-03-11
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19325   155228031    7  HPFS/NTFS
/dev/sda2           19327       19457     1052257+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dbbf88b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       50602   406460533+   7  HPFS/NTFS
/dev/sdb2           55702       60802    40960000    7  HPFS/NTFS
/dev/sdb3           50603       55701    40957717+  83  Linux

---

### Post by theozzlives on 2009-03-11
you have 2 NTFS and 1 ext3 on your external, look for sdb

---

### Post by XSoph on 2009-03-11
Well, I have, but the installer isn't listing anything but the /sda volumes at the step where you select the installation partition. Is that where you're telling me to look?

---

### Post by XSoph on 2009-03-11
Let me see if I can get a screenshot up.

---

### Post by XSoph on 2009-03-11
[IMG]http://img17.imageshack.us/img17/3307/prepare.png[/IMG]
[IMG]http://img17.imageshack.us/img17/4483/screenshotinstall.png[/IMG]

---

### Post by taurus on 2009-03-12
Are you using intrepid LiveCD (8.10)?  Reboot and start over again to see if the installer is picking up /dev/sdb this time.

---

### Post by XSoph on 2009-03-12
I think I fixed it. It seems to me that the installer only looks for a 'primary' partition on a drive. My primary had been my general storage partition. I reformatted the drive completely, first backing up the data I had stored, then made the ext3 partition _first_ as well as making it primary. I rebooted and the installer picked up the new ext3 partition.

Thanks , Taurus. I hope this helps someone else.

---

