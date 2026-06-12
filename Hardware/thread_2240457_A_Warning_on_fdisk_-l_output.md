---
title: "A Warning on fdisk -l output"
date: 2014-08-20
forum: Hardware
---

### Post by rickm1945 on 2014-08-20
I ran sudo fdisk -l and got his output. anybody know what this warning is and what should I do about it.
```
richard@richard-Studio-XPS-8100:~$ sudo fdisk -l
[sudo] password for richard: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xeea60b3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009663e

```

---

### Post by westie457 on 2014-08-20
Hi, don't do anything about it.

Your hard-drive has a 'GPT' partition table and is working normally.
If you want to see the partitions in the drive use ```
sudo parted -l
```

Here is an article about GPT partition table. [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by rickm1945 on 2014-08-20
Thank you  for the response.

---

