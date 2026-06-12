---
title: "Reformatting brick hard drive"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by Stoodle on 2007-10-27
I was trying to install Ubuntu on my external hard drive but I haven't quite managed it yet ( I know about the tutorial on these forums). I wanted to instead put stuff on there and do install linux later but my problem is that it's kinda bricked. I can' write (and I don't think read) it. I used fdisk and I think I changed the partitions to ext2 (couldn't find ext3) but I can't wipe it. Therefore, I can't write to it. Help!

This is what I'm getting:

$ sudo fdisk /dev/sda1

The number of cylinders for this disk is set to 476937.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): p

Disk /dev/sda1: 500.1 GB, 500105217024 bytes
64 heads, 32 sectors/track, 476937 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

     Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-476937, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-476937, default 476937): 
Using default value 476937

Command (m for help): p

Disk /dev/sda1: 500.1 GB, 500105217024 bytes
64 heads, 32 sectors/track, 476937 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1               1      476937   488383472   83  Linux

Command (m for help): d
Selected partition 1

Command (m for help): p

Disk /dev/sda1: 500.1 GB, 500105217024 bytes
64 heads, 32 sectors/track, 476937 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

     Device Boot      Start         End      Blocks   Id  System

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-476937, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-476937, default 476937): 
Using default value 476937

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 83

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

---

### Post by Stoodle on 2007-11-10
Bump. Help! I'm not sure how to reformat it using fdisk, or anything really. My Windows computer doesn't recognize it and I don't know how to do  anything with it on Linux.

---

### Post by AJB2K3 on 2007-11-10
Does the live cd not work? I use the gui formatter on the live cd.

---

### Post by Stoodle on 2007-11-10
Well I had considered using that...But wait, for an external hard drive? Anyway, I had thought that Linux came with something for partitioning and reformatting.

---

