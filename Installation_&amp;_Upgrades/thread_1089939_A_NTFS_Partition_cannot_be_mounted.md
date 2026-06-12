---
title: "A NTFS Partition cannot be mounted"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by T1000 on 2009-03-07
I installed Intrepid Ibex 64 on the sdb3 partition of my second Hard Disk Drive.

I can mount and see the NTFS Windows partitions of my first HDD under Ubuntu, what is great.

My problem is that the Windows NTFS partition of the second HDD cannot be accessed. i.e. the NTFS configuration tool will not see it. I installed Disk manager as well, without any improvement.


fdisk -l reports the following, where sdb1 is the invisible partition

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x996bd1f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28880   231971808+   7  HPFS/NTFS
/dev/sda2           28880       30401    12223488    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d5546d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19453   156255198+   7  HPFS/NTFS
/dev/sdb2           19454       19939     3903795   82  Linux swap / Solaris
/dev/sdb3   *       19940       30401    84036015   83  Linux

Furthermore, /etc/fstab includes the following:
# /dev/sdb1
UUID=B43AAF5E3AAF1C7C /dev/sdb1       ntfs    defaults,umask=007,gid=46 0       1

Any clue?
Thanks for any help!

---

### Post by taurus on 2009-03-07
> **T1000 said:**
> I installed Intrepid Ibex 64 on the sdb3 partition of my second Hard Disk Drive.

I can mount and see the NTFS Windows partitions of my first HDD under Ubuntu, what is great.

My problem is that the Windows NTFS partition of the second HDD cannot be accessed. i.e. the NTFS configuration tool will not see it. I installed Disk manager as well, without any improvement.


fdisk -l reports the following, where sdb1 is the invisible partition

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x996bd1f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28880   231971808+   7  HPFS/NTFS
/dev/sda2           28880       30401    12223488    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d5546d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19453   156255198+   7  HPFS/NTFS
/dev/sdb2           19454       19939     3903795   82  Linux swap / Solaris
/dev/sdb3   *       19940       30401    84036015   83  Linux

Furthermore, /etc/fstab includes the following:
# /dev/sdb1
UUID=B43AAF5E3AAF1C7C **[COLOR="Red"]/dev/sdb1[/COLOR]**       ntfs    defaults,umask=007,gid=46 0       1

Any clue?
Thanks for any help!

That is the wrong mount point.  You should replace it with something like **[COLOR="Blue"]/media/sdb1[/COLOR]** instead.  Of course, don't forget to create the new mount point or it won't be able to mount again when you reboot.

```
sudo mkdir /media/sdb1
```

---

### Post by T1000 on 2009-03-08
Thanks

---

