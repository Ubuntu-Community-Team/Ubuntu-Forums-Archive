---
title: "RAID1 problems /swap almost there"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by oly on 2007-05-27
I have set up a raid system with 2 250gb hard disks in raid1, how ever it does not seem to be working 100%, for one cat /proc/mdstat returns what i would expect where as fdisk -l returns 3 partitions missing the 4th which is my swap partition.

If i run system monitor it stats that my swap space is 0 bytes.

cat /proc/mdstat returns
```

Personalities : [raid1] 
md3 : active raid1 sda5[0] sdc5[1]
      179735104 blocks [2/2] [UU]
      
md2 : active raid1 sda3[0] sdc3[1]
      979840 blocks [2/2] [UU]
      
md1 : active raid1 sda2[0] sdc2[1]
      48829440 blocks [2/2] [UU]
      
md0 : active raid1 sda1[0] sdc1[1]
      14651136 blocks [2/2] [UU]
      
unused devices: <none>


```

fdisk -l returns
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  fd  Linux RAID autodetect
/dev/sda2            1825        7903    48829567+  fd  Linux RAID autodetect
/dev/sda3            7904        8025      979965   fd  Linux RAID autodetect
/dev/sda4            8026       30401   179735220    5  Extended
/dev/sda5            8026       30401   179735188+  fd  Linux RAID autodetect

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    5  Extended
/dev/sdb5               1        7833    62918509+  83  Linux
/dev/sdb6            7834       19457    93369748+  83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1824    14651248+  fd  Linux RAID autodetect
/dev/sdc2            1825        7903    48829567+  fd  Linux RAID autodetect
/dev/sdc3            7904        8025      979965   fd  Linux RAID autodetect
/dev/sdc4            8026       30401   179735220    5  Extended
/dev/sdc5            8026       30401   179735188+  fd  Linux RAID autodetect

Disk /dev/md0: 15.0 GB, 15002763264 bytes
2 heads, 4 sectors/track, 3662784 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 50.0 GB, 50001346560 bytes
2 heads, 4 sectors/track, 12207360 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md3: 184.0 GB, 184048746496 bytes
2 heads, 4 sectors/track, 44933776 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

    Device Boot      Start         End      Blocks   Id  System
/dev/md3p1               1    44933776   179735102    5  Extended


```
ie missing /dev/md2 which is the partition i created to be /swap

sudo fdisk /dev/md2 returns
Unable to read /dev/md2

if i try and recreate the raid with mdadm it says that bot swap partitions are in use.

any ideas on what i can try next ?

---

### Post by kidders on 2007-05-28
Hi there,

This is quite a weird setup! The idea of spreading multiple RAID arrays over two devices seems inherently unwise to me. Additionally, I can't think of a reason for superimposing *swap* on RAID. :confused:

Can you post the contents of your /etc/fstab? (I'm hoping the reason for your problem is in there somewhere.)

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

