---
title: "Error: Can't have a partition outside the disk! need help"
date: 2014-11-01
forum: Hardware
---

### Post by Peter_R._Larsen on 2014-11-01
I harddisk on sdc with unallocated on Gparted
and on terminal shows extended, and i want to delete extended partition and tried to fix from gparted website tried didnt understand it (forgive my bad english)

sudo fdisk -l
```
Disk /dev/sdc: 1000.2 GB, 1000204884480 bytes255 heads, 63 sectors/track, 121601 cylinders, total 1953525165 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x618ec1eb


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   776503295   388250624   83  Linux
/dev/sdc2       979961856  1953525167   486781656    7  HPFS/NTFS/exFAT
/dev/sdc3       776507390   979959807   101726209    5  Extended
/dev/sdc5       781252608   796878847     7813120   82  Linux swap / Solaris
/dev/sdc6       796880896   979959807    91539456   83  Linux
/dev/sdc7       776507392   781252607     2372608   82  Linux swap / Solaris


Partition table entries are not in disk order



```

with sudo parted -l
```
Model: ATA Hitachi HTS54505 (scsi)Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type     File system     Flags
 1      1049kB  100GB  100GB   primary  ntfs            boot
 2      100GB   108GB  8000MB  primary  linux-swap(v1)
 3      108GB   500GB  392GB   primary  ext4




Error: Can't have a partition outside the disk! 
```

sdc shows Error: Can't have a partition outside the disk!

---

### Post by yancek on 2014-11-01
I'm not sure what you are hoping to accomplish with that.  You do understand that if you delete sdc3 which is your Extended partition, sdc5, 6 and 7 will also be gone because they are logical partitions within the Extended partition.  You have a large Linux partition at the beginning of the drive (sdc1) then your Extended partition and a windows partition at the end of the disk.  Looking at the sectors, there doesn't seem to be much unallocated space on the drive.  What exactly are your intentions, your end goal?

---

### Post by Peter_R._Larsen on 2014-11-02
> **yancek said:**
> I'm not sure what you are hoping to accomplish with that.  You do understand that if you delete sdc3 which is your Extended partition, sdc5, 6 and 7 will also be gone because they are logical partitions within the Extended partition.  You have a large Linux partition at the beginning of the drive (sdc1) then your Extended partition and a windows partition at the end of the disk.  Looking at the sectors, there doesn't seem to be much unallocated space on the drive.  What exactly are your intentions, your end goal?

I want to fix sdc3 which is now sdb3 shown on terminal
```
Device Boot      Start         End      Blocks   Id  System/dev/sdb1   *        2048   776503295   388250624   83  Linux
/dev/sdb2       979961856  1953525167   486781656    7  HPFS/NTFS/exFAT
/dev/sdb3       776507390   979959807   101726209    5  Extended
/dev/sdb5       781252608   796878847     7813120   82  Linux swap / Solaris
/dev/sdb6       796880896   979959807    91539456   83  Linux
/dev/sdb7       776507392   781252607     2372608   82  Linux swap / Solaris


Partition table entries are not in disk order


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes



```

I want to delete or remove, fix sdb3 extended, because on gparted it shows unallocated (cant upload the picture)
cause i want to change some size of partition on sdb

---

### Post by yancek on 2014-11-02
Before you delete sdc3, or whatever the Extended shows as, you need to first delete the logical partitions within it:  sdc5, sdc6 and sdc7.  This will of course, totally destroy any data on all of those partitions.  If you don't have anything on them, no problem.  If you do, you need to move it somewhere else.  You can do this in gparted by first unmounting the partitions from the Partition tab and then selecting Delete.  Make sure you get the right drive.  It can change from sdc to sdb if you remove a drive, hard drive or flash drive so don't have anything else attached and make sure you have the same partitions so you get the correct drive.  I'm still not sure why you want to do this.  There isn't much unallocated space that I can see from the sector output but if you don't have any data on it, should not matter.  Does this have to do with the error you reported?  How and when do you see that?
 
Error: Can't have a partition outside the disk! need help

---

### Post by Peter_R._Larsen on 2014-11-02
> **yancek said:**
> Before you delete sdc3, or whatever the Extended shows as, you need to first delete the logical partitions within it:  sdc5, sdc6 and sdc7.  This will of course, totally destroy any data on all of those partitions.  If you don't have anything on them, no problem.  If you do, you need to move it somewhere else.  You can do this in gparted by first unmounting the partitions from the Partition tab and then selecting Delete.  Make sure you get the right drive.  It can change from sdc to sdb if you remove a drive, hard drive or flash drive so don't have anything else attached and make sure you have the same partitions so you get the correct drive.  I'm still not sure why you want to do this.  There isn't much unallocated space that I can see from the sector output but if you don't have any data on it, should not matter.  Does this have to do with the error you reported?  How and when do you see that?
 
Error: Can't have a partition outside the disk! need help

i hope you can see this pic
if not, how do i? 
[IMG]https://www.facebook.com/photo.php?fbid=349017871926806&set=a.349017991926794.1073741826.100004557887161&type=1&theater[/IMG]

---

### Post by Peter_R._Larsen on 2014-11-02
> **yancek said:**
> Before you delete sdc3, or whatever the Extended shows as, you need to first delete the logical partitions within it:  sdc5, sdc6 and sdc7.  This will of course, totally destroy any data on all of those partitions.  If you don't have anything on them, no problem.  If you do, you need to move it somewhere else.  You can do this in gparted by first unmounting the partitions from the Partition tab and then selecting Delete.  Make sure you get the right drive.  It can change from sdc to sdb if you remove a drive, hard drive or flash drive so don't have anything else attached and make sure you have the same partitions so you get the correct drive.  I'm still not sure why you want to do this.  There isn't much unallocated space that I can see from the sector output but if you don't have any data on it, should not matter.  Does this have to do with the error you reported?  How and when do you see that?
 
Error: Can't have a partition outside the disk! need help

ok finally upload, here is the problem, that shows gparted and it work find windows showing ntfs and on linux'

[IMG]http://profile.ultimate-guitar.com/profile_mojo_data/2/2/5/9/2259229/pics/_c1285412_image_0.png[/IMG]

---

### Post by oldfred on 2014-11-02
I think this is the problem.

 Drive total 195352[COLOR=#ff0000]5165[/COLOR] sectors
/dev/sdc2       979961856  195352[COLOR=#ff0000]5167[/COLOR]   486781656    7  HPFS/NTFS/exFAT

Or sdc2 ends after the end`of the drive by two sectors.

Often fixparts is the easiest way to fix this issue.
      
 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by westie457 on 2014-11-02
The problem is the second partition is too big. Shrink that by a small amount. Gparted should then show all partitions.

---

