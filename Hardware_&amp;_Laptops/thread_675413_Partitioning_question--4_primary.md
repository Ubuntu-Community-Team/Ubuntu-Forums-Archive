---
title: "Partitioning question--4 primary"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by deavik on 2008-01-22
Hello, I am having trouble with my partition tables. I had 3 primary and 1 extended partition, but then I backed up and deleted one of the partitions in the extended partition. Now I cannot do anything with the free space... is there any way to put it in the extended partition from gparted? (screenshot below) Obviously Gparted says I can create another partition because I have 4 primary. But I just want it as a logical.

Here is the output of fdisk -l
```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcacdcacd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         333        1989    13309852+   7  HPFS/NTFS
/dev/hda2               1         332     2666758+  12  Compaq diagnostics
/dev/hda3            1990        3392    11269597+  83  Linux
/dev/hda4            5687        7296    12932325    5  Extended
/dev/hda5            5942        7296    10884006    7  HPFS/NTFS
/dev/hda6            5688        5941     2040223+  82  Linux swap / Solaris

Partition table entries are not in disk order

```
This screen capture from Gparted shows the problem better: [IMG]http://img115.imageshack.us/img115/6830/parttablesc4.png[/IMG]

Thanks for any help!

---

### Post by logos34 on 2008-01-22
I've never seen gparted do that--it looks like the extended just snapped back like a rubber band, leaving only a small empty space in front of swap inside, and most of the space outside.  

To resize the extended back to the **left** you'll need the [gparted live cd (_>_ 0.3.4)]("http://gparted-livecd.tuxfamily.org/").  Plus you need to work from live cd because I don't think it will let you do anything to hda4 if any partitions, even swap, is mounted.

---

### Post by deavik on 2008-01-23
I don't know what partitioner the installer uses, but it's more powerful i guess :)

I reinstalled and set up the partition, it wasn't a big deal since I had just installed anyway

Thanks

---

