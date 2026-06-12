---
title: "How can I increase the size of an existing partition"
date: 2008-12-01
forum: General Help
---

### Post by yinglcs2 on 2008-12-01
Hi, 

I use GParted to view my drive partition:

/dev/sdc1   ext3   27.97 GB
/dev/sdc2   linux-swap   1.86 GB
/dev/sdc3   ext3   8.72 GB
/dev/sdc4   ext3   30.27 GB
unallocated unallocated 42.97GB

How can I 
1) add the 42.97 GB to /dev/sdc4? I don't see how to do that in GParted?
2) Create a new partition for the unallocated 42.97 GB. I get this error when i try to do that in GParted:

It is not possible to create more than 4 primary partitions

If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first.

I have data in all existing partition. I don't want to lose the data. 
Thank you for any help.

---

### Post by logos34 on 2008-12-01
You can only expand sdc4 to incorporate the unallocated space as long as the two are contiguous.  If sdc4 is your / partition, then you'll have to do it with gparted on the live cd because root cannot be mounted.

If instead you want to create an extended partition in order to take up the empty space, you'll have to backup the data on one of the partitions, delete it, create the extended with logical partitions inside, then restore the data to one of the new partitions

what does

sudo fdisk -l

show?

---

### Post by yinglcs2 on 2008-12-13
Thank you for your help.

I think the easiest way is to increase the size of my /dev/sdc4/. But gparted does not let me do it. Can you please tell me what to do? I prefer not to lose/copy my data on /dev/sdc4 (i don't have that much space to copy to).

Here is the command result that you suggest me to do:

sudo fdisk -l
 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3825       11576    62267940    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           11577       12161     4694760   12  Compaq diagnostics
Partition 3 does not end on cylinder boundary.
/dev/sda5            9665        9677      104391   83  Linux
/dev/sda6            9678       11576    15253686   83  Linux
/dev/sda7            3825        5651    14675314+  83  Linux
/dev/sda8            5652        5955     2441848+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44e4be6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         304     2441848+  82  Linux swap / Solaris
/dev/sdb2             305        4013    29792542+  83  Linux
/dev/sdb3            4014        7296    26370697+  83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000326

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3651    29326626   83  Linux
/dev/sdc2            3652        3894     1951897+  82  Linux swap / Solaris
/dev/sdc3            3895        5032     9140985   83  Linux
/dev/sdc4            5033        8984    31744440   83  Linux
~>

---

### Post by logos34 on 2008-12-13
You unmounted sdc4, and gparted still won't let you grow it?

---

### Post by yinglcs2 on 2009-01-04
Thank you.

I have a related question. Is it possible to combine /dev/sdc3 with /dev/sdc4? My sdbc3 only have 9 GB but my sdc4 has 40 Gb. I can clear all files from sdbc3 but how can i add the 9 Gb to sdc4?

Thank you.


```

~> sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3825       11576    62267940    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           11577       12161     4694760   12  Compaq diagnostics
Partition 3 does not end on cylinder boundary.
/dev/sda5            9665        9677      104391   83  Linux
/dev/sda6            9678       11576    15253686   83  Linux
/dev/sda7            3825        5651    14675314+  83  Linux
/dev/sda8            5652        5955     2441848+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44e4be6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         304     2441848+  82  Linux swap / Solaris
/dev/sdb2             305        4013    29792542+  83  Linux
/dev/sdb3            4014        7296    26370697+  83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000326

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3651    29326626   83  Linux
/dev/sdc2            3652        3894     1951897+  82  Linux swap / Solaris
/dev/sdc3            3895        5032     9140985   83  Linux
/dev/sdc4            5033        8984    31744440   83  Linux


```

---

### Post by logos34 on 2009-01-04
> **yinglcs2 said:**
> 
I have a related question. Is it possible to combine /dev/sdc3 with /dev/sdc4? My sdbc3 only have 9 GB but my sdc4 has 40 Gb. I can clear all files from sdbc3 but how can i add the 9 Gb to sdc4?

Thank you.


```

/dev/sdc3            3895        5032     9140985   83  Linux
/dev/sdc4            5033        8984    31744440   83  Linux

```

Move/backup the files on sdc3 to another location.  Unmount and delete sdc3.  Then unmount sdc4, and drag the left boundary over to reclaim the empty space that was formerly sdc3.  (If one of them is /, then you'll obviously have to work from the ubuntu live cd because root cannot be mounted during resize).  Remove the sdc3 entry from /etc/fstab.

If you have any problems, post back with questions

---

