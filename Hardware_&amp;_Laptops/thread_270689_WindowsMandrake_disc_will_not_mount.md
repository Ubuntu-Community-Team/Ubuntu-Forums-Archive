---
title: "Windows/Mandrake disc will not mount"
date: 2006-10-03
forum: Hardware &amp; Laptops
---

### Post by erasmus2006 on 2006-10-03
Hi there,
When my version of Mndrake got corrupted by partial updates and dependency problems (long story) I added a new primary drive and loaded Ubuntu, making the Windows/Mandrake disc the slave. I can see it in Gparted, although some partitions say the file structure is unknown. When I try to mount the disc, it tells me "special device not found". I've got a lot of data on the slave disk that I would like to access. Anyone got any ideas?
Thanks, Erasmus2006.

---

### Post by mangoti on 2006-10-03
Maybe you should try to mount a partition instead of the disk itself. Can you tell about the layout for your HD?

---

### Post by erasmus2006 on 2006-10-03
hi there,

I did try to mount just a partition with no success. I've done a snapshot of Gparted. which I've attached.
Cheers

---

### Post by mangoti on 2006-10-03
What are the unknown partition supposed to be? What is the output of "sudo fdisk -l"?

Seems to me that you have a problem with the partition table.

---

### Post by erasmus2006 on 2006-10-04
Hi there,

This is what the fdisk command gives me!

Thanks.

Disk /dev/hda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32        1216     9518512+   5  Extended
/dev/hda5              32        1216     9518481   8e  Linux LVM

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?           1        2432    19535008+   c  W95 FAT32 (LBA)
/dev/hdb2            2433       10011    60878317+   5  Extended
/dev/hdb5            2433        3196     6136798+  83  Linux
/dev/hdb6            5109        5872     6136798+  83  Linux
/dev/hdb7            5873        5935      506016   82  Linux swap / Solaris
/dev/hdb8            5936       10011    32740438+  83  Linux
/dev/hdb9            3197        3336     1124518+  82  Linux swap / Solaris
/dev/hdb10           3337        5108    14233558+  83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3936     1007600    e  W95 FAT16 (LBA)

---

### Post by mangoti on 2006-10-10
Hi,

Sorry, I've been away for the long week-end. Hope you already find an answer to your trouble. If not, you should try to fix the partition order (I think fdisk can do that; I dont have a linux box at hand now so I cant tell). Looks like /dev/hdb5 was divided into 3 partitions after hdb6 to hdb8 have been created.
Good luck.

---

