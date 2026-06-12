---
title: "CFDISK complains about HDD partitions"
date: 2010-02-16
forum: Hardware
---

### Post by SaintDanBert on 2010-02-16
When I fun CFDISK on my laptop HDD, it complains
```

user@host$ sudo cfdisk /dev/sda

FATAL ERROR: Bad logical partition 6: 
             enlarged logical partitions overlap

Press any key to exit cfdisk

```

Using other tools I don't have the same trouble:
```

user@host$ sudo fdisk -l /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe11595f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15298   122881153+   7  HPFS/NTFS
/dev/sda2           15299       16700    11261565   12  diagnostics
/dev/sda3           16701       60801   354241282+   5  Extended
/dev/sda5           52516       60801    66557295    7  HPFS/NTFS
/dev/sda6           16701       24602    63472752   83  Linux
/dev/sda7           24603       24845     1951866   83  Linux
/dev/sda8           24846       26061     9767488+  83  Linux
/dev/sda9           44613       52514    63472783+  83  Linux

Partition table entries are not in disk order


```
--and--
```

user@host $ sudo df -H
Filesystem             Size   Used  Avail Use% Mounted on
...
/dev/sda6               64G   5.8G    56G  10% /
/dev/sda7              2.0G    97M   1.8G   6% /boot
/dev/sda8              9.9G   3.2G   6.2G  35% /var
/dev/sda9               64G   8.8G    52G  15% /home
/dev/sda5               69G    13G    56G  18% /media/DatNTFS00
/dev/sda1              126G    20G   106G  16% /media/SysWinXPpro

```

It looks like I'm missing some space but dashed if I can find it.

~~~ 0;-Dan

---

### Post by viper250 on 2010-02-16
cfdisk shows error possibly because the partition may be too large
fdisk -l shows that sda3 and sda5 both end on the same block
this may be causing the partition overlap that shows in cfdisk
each partition program tends to show the info differently
try downloading parted magic and see what it displays
you may be able to correct the errors with parted magic

---

### Post by SaintDanBert on 2010-02-16
> **viper250 said:**
> 
...
fdisk -l shows that sda3 and sda5 both end on the same block
this may be causing the partition overlap that shows in cfdisk 
...

**sda3** is an extended partition -- home for "logical partitions."
**sda5** is a logical partition that happens to end on the last parts of the extended partition. Naturally, they would end on the same place.

The **cfdisk** complaint was about **sda6**...

Could this be caused by the simple fact that in partition order: sda3, sda5, sda6, ... the block details are also not in ascending order?

> **viper250 said:**
> 
each partition program tends to show the info differently
try downloading parted magic and see what it displays
you may be able to correct the errors with parted magic

I've never heard of "parted magic".  I am aware of the win-dose program, PartitionMagic(tm). I think it is from Symantec (aka, Norton).

Thanks,
~~~ 0;-Dan

---

### Post by efflandt on 2010-02-17
Just curious why your partitions are not in physical order.  Maybe that is what it is trying to tell you, but does not have proper words for it.

---

