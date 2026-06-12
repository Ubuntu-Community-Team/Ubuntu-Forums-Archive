---
title: "how to convert a logical partition to a primary ?"
date: 2008-07-24
forum: General Help
---

### Post by dexter.deepak on 2008-07-24
here is my fdisk:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551       19457   135805477+   f  W95 Ext'd (LBA)
/dev/sda5            5101        8924    30716248+   b  W95 FAT32
/dev/sda6            8925       14023    40957686    7  HPFS/NTFS
/dev/sda7            2551        2672      979902   82  Linux swap / Solaris
/dev/sda8            2673        5100    19502878+  83  Linux
/dev/sda9           14024       16455    19535008+  83  Linux
/dev/sda10          16456       19457    24113533+  83  Linux

```

i need to install solaris now..on sda8/9 ,but as it demands a primary parition, i want to convert sda8/9 , which are part of sda2(extended), to primary..i cant afford to lose any data on other partitions.

please help me..

---

### Post by vanadium on 2008-07-24
Not directly possible. A theoretical possibility is to make an images of the extend partition, then repartition the drive and place the image back in the primary partition designed to host the data.

It is just a theoretical possibility. In your case, you probably would have to move out all of your logical partitions out before you can move/resize the extended partition to create room for more primary partitions.

Be aware that you can have at most 4 primary partitions, or three primary partitions and one extended.

---

