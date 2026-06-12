---
title: "Installed 8.04 only partial HDD shown"
date: 2008-11-05
forum: General Help
---

### Post by Joe2Shoe on 2008-11-05
I installed 8.04 on my 160GB HDD.  Somehow I forgot to partition the rest of the HDD (about 120GB), after creating the neccesary partitions, and the 120GB does not show up in File System.
How do I partition the remaining 120GB without reinstalling 8.04?
Thank you for your assistance.
Joe2Shoe.

---

### Post by Titan8990 on 2008-11-05
Depends on what you prefer. I would use fdisk. First you need to find out the name that is given to the drive using fdisk -l:

```
Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c310fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 250.0 GB, 250057219584 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3151

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29920   240332368+  83  Linux
/dev/sdb2           29921       30401     3863632+  82  Linux swap / Solaris
```

If /dev/sda is the one I would like to add a partition to:

sudo fdisk /dev/sda


Hit n and then enter to add a new partition. Accept all the defaults because it will be the remainder of the drive.

When finished hit w and enter to write the changes to the disk. Now it will need to be formatted (example assumes the partition you just made is /dev/sda2):

sudo mke2fs -j /dev/sda2


An alternative would be to use a GUI program (boo):

sudo apt-get install gparted


Good luck.

---

### Post by Joe2Shoe on 2008-11-05
Titan,
I appreciate your quick blessings.
I figured it out, though, in the meantime.
I downloaded/installed and ran GParted.
Was quite simple, really.
Thanks again, brother.
Joe2Shoe.

---

### Post by Titan8990 on 2008-11-06
Anytime. and don't forget to mark your thread as solved.

---

