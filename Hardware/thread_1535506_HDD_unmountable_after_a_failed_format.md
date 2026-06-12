---
title: "HDD unmountable after a failed format"
date: 2010-07-21
forum: Hardware
---

### Post by mac00l on 2010-07-21
Here's the story.

I have several old (and I mean really old) computers lying around the house. So one day I decided to gather all the junk, and build my own frankenstein to keep as a remote media center.

So here I am formatting all those old HDD, and I'm with the last one right now, and after a failed format from Lucid Lynxs I'm unable to force mount, or do anything with the HDD. I want to make something like a force format, or anything that will let me mount the HDD in another computer. The SDB is the one I want to force mount, format, or whatever, what else can I do?
Here are my logs:

> macbeath@MacBeath:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xea3d3c3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       29353   235667456    7  HPFS/NTFS
/dev/sda3           29354       38913    76790700    5  Extended
/dev/sda5           29354       38913    76790668+  83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaa5a8a3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5168    39070048+   7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf58a0350

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001    7  HPFS/NTFS


---

### Post by IcarusR on 2010-07-21
Have you tried mounting it manually from a terminal ??

```
sudo mount -t ntfs /dev/sdb1 /home/your_user_name/some_mount_point
```

Obviously you need to input your username & a mount point that exists.

I am not aware of a way to 'force' mount a drive.

---

