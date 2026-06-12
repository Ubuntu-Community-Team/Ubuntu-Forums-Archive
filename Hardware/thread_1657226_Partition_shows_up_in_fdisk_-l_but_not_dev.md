---
title: "Partition shows up in fdisk -l but not /dev"
date: 2010-12-31
forum: Hardware
---

### Post by zyberwoof on 2010-12-31
I have a computer with one HDD for the OS and then a bunch for a LVM array.  Both of those still work fine.  I added a new HDD to the machine with the purpose of adding it to the LVM array.  Unfortuantely, I can't add it to the array.  After some basic troubleshooting I noticed that its one and only partition shows up under **sudo fdisk -l /dev/sda**, but not in /dev.

The result of running sudo fdisk -l /dev/sda is:
```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d737678

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      182401  1465136001   8e  Linux LVM
```

My partiton on sda shows up fine and is listed with a partiton type of "8e Linx LVM" (I set it up like that with fdisk).

When I look in /dev I get sda, but not sda1.  
```
me@hostname:/dev$ ls sd*
sda  sdb1  sdc1  sdd1  sde1  sdf1  sdg1  sdh1  sdi1  sdi3
sdb  sdc   sdd   sde   sdf   sdg   sdh   sdi   sdi2
```

I have tried running fdisk on /dev/sda multiple times blowing away the partition and recreating it in a hope that it will show up in dev, but no luck.

---

