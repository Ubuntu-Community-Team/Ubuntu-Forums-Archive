---
title: "Installer and GParted do not see any partitions!"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by informer2000 on 2009-10-31
I'm trying to install Karmic on my laptop from the LiveCD but the installer just doesn't seem to find my disk drive's partitions. It identifies the entire thing as unallocated. GParted as well as the alternative installer CD have the same issue. I can mount the partitions and work with them without any problems from the LiveCD, but for some strange reason the installer doesn't see them.

Here's the output of fdisk:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x227397db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   521375734   260687836    7  HPFS/NTFS
/dev/sda2       521389575   562339254    20474840   83  Linux
/dev/sda3       562339323   566532202     2096440   82  Linux swap / Solaris
/dev/sda4       566532225   625153409    29310592+   f  W95 Ext'd (LBA)
/dev/sda5       566532288   603288943    18378328   83  Linux
/dev/sda6       603295744   625135615    10919936    7  HPFS/NTFS


I have 2 NTFS partitions: one for Vista (which isn't there any more) and another for the recovery software. I also have 3 other partitions from my previous installation. One of them is my /home (which I want to maintain). TestDisk doesn't seem to find any problems with the partitions. One strange thing is that Palimpsest Disk Utility that comes with the LiveCD identifies an unallocated space of 18446744073704 GB!

cfdisk reports:
FATAL ERROR: Bad primary partition 3: Partition ends after end-of-disk

Any help would be greatly appreciated..

---

### Post by sstalpers on 2009-11-17
I got the same error and fixed it by deleting the last partitions on my harddisk. cfdisk -l gave a "FATAL ERROR: partition 3 ends after end-of-disk". I saw several earlier threads on the problem but without solutions. For others having the same problem, here's how I fixed it. Not elegant but does the job:

1. Back up ALL of your harddisk - always a good idea when you start messing with partitions! In particular back up the partition causing the problem, because it will be erased. You can simply copy your data to an external harddisk or use e.g. [Clonezilla live]("http://clonezilla.org/") to make an image of your disk.

2. boot up from a livecd. I used [SystemRescueCD]("http://www.sysresccd.org/") but an Ubuntu livecd should also work.

3. Delete the partitions causing the problem. I guess this is usually the last (extended) partition. The basic commands are: ```
fdisk /dev/sdb
p
d
4
w
``` This starts fdisk for the affected disk (here: sdb), prints the partition table, deletes the affected (here: 4th) partition on hard disk, and writes the changes to the partition table. [Here]("http://www.cyberciti.biz/faq/linux-how-to-delete-a-partition-with-fdisk-command/") are more instructions how to use fdisk.

4. Optionally recreate partitions with gparted and recover partition images using clonezilla. I used gparted because the fdisk manual page recommends it (or parted or cfdisk) over fdisk for large harddisks. 

I am sure there is a much more elegant way to solve this problem. E.g. by resizing partitions? But parted would not start because of the error (I have no clue how to use parted with the -z option) and AFAIK fdisk does not allow you to keep data when resizing partitions. 

In my particular case, the problem started when I installed Windows XP on my 2nd harddisk after which cfdisk and parted gave the error "overlapping partitions". I fixed the overlap using testdisk (on SystemRescueCD) but then got the 'partition ends after end-of-disk' error. In my case it was the last extended partition containing 2 logical partitions that were the problem.

---

### Post by oldfred on 2009-11-17
On my system it saw the partitions but they were greyed out. I had to go back to windows and run check disk which found several errors. Also windows has to be totally shut down normally, I have had issues mounting the NTFS partition where windows closed abnormally.

---

