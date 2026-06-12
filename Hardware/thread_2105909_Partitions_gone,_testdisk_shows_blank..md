---
title: "Partitions gone, testdisk shows blank."
date: 2013-01-17
forum: Hardware
---

### Post by LoopTown on 2013-01-17
Hy!  I tried to install new HDD, upgrading 250GB to 320 and using 250GB as external. First I tried to format 320 into ext4 with Gparted witch showed it succeeded in doing this and the drive is now ext4 and then showed it\s unallocated. Next I hoped maybe just trying to copy the old drive onto the new one I can later on installing ubuntu again format the drive in installation. When I tried to copy the partition It disappeared. The whole drive changed to unallocated. I tried to restore ext4 and an old ntfs partitions using testdrive but when testdrive found partitions and showed that the end of partition is lost and should I overwrite I choosed yes. Now even testdrive can\t find partitions.   Can I still restore ANY information on my drive?  All help greatly appreciated!!!

---

### Post by LoopTown on 2013-01-17
While writing the new endpoint it also changed the name from sdc into sde witch now shows the ntfs partition again but also shows that it has no endpoint. After analyze it shows I have three Linux partitions but I have 1 NTFS and 1 ext4 (where is also swap).

I\m lost. Anyone?

---

### Post by oldfred on 2013-01-17
External drives will change drive number with unmounts & remounts if not rebooting. So any command that is on a device like /dev/sdf, double & triple check that you are working on correct device.

Post this 

sudo fdisk -lu

---

### Post by LoopTown on 2013-01-17
The problem is I can\t even mount the disk (as far as gparted is concerned).

Following goes for the disk in question
> Disk /dev/sde: 250.1 GB, 250059348992 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00bc7ad1

Disk /dev/sde doesn't contain a valid partition table
Thank you for reply!

PS! Right now running testdisk analyzer for ntfs (trying to find my ext4 and tought this my help). It does show two partitions one being ntfs and the other linux swap.

---

### Post by LoopTown on 2013-01-17
testdisk>
> TestDisk 6.14-WIP, Data Recovery Utility, December 2012
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sde - 250 GB / 232 GiB - CHS 30401 255 63

The harddisk (250 GB / 232 GiB) seems too small! (< 262 GB / 244 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  Linux                28695 213 63 31851 232 61   50702336
   Linux                28699 136 46 31855 155 44   50702336
   Linux                28701 179 23 31857 198 21   50702336








[ Continue ]
ext4 blocksize=4096 Large file Sparse superblock Recover, 25 GB / 24 GiB


---

### Post by dabl on 2013-01-17
> **LoopTown said:**
>  First I tried to format 320 into ext4 with Gparted witch showed it succeeded in doing this and the drive is now ext4 and then showed it\s unallocated.

I think you went wrong here -- this sentence does not make sense.  A partition shown as "unallocated" by gparted cannot hold a filesystem (a "format" in Windows-speak).

A new hard drive typically does not have a partition table on it.  So Step 1 is, in GParted, go to "Device > New Partition Table", accept the default ms-dos type, and "OK".  Then Step 2 is to right click in the unallocated space and choose "new" to make a new partition.  Then you can decide how big it should be, and what the filesystem should be.  Note that the commands are not executed until you click "Apply" on the upper menu.

Or, if you have an existing partition on another hard drive that you would like to copy onto an unallocated drive, GParted will let you do to that with a simple copy and paste.  But it takes a long time -- it's not a fast process.

Hope that helps next time around.

---

### Post by LoopTown on 2013-01-17
Thank you alot!

I used HDD that I stole from my old laptop but deleted everything (including tables). Wich I didn\t know was that I have to make the format table first. 
My purpose is to copy everything anyways (if I can get everything restored) so then I don\t have to make tables?

BTW gparted does all the process of creating format even without tables.
(Witch doesn\t work later on)

Thanks You for educating me!

---

### Post by dabl on 2013-01-17
Every drive needs a partition table, even if there's only one partition on it.  No partition table = no filesystem = no data.

---

### Post by LoopTown on 2013-01-18
Managed to find filesystems (thank god for testdisk) and write new tables. Now everything is back to normal. 

Big thanks to everyone who helped!

---

