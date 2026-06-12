---
title: "Drive Problem Partition Name Misread"
date: 2012-10-06
forum: Hardware
---

### Post by Loki*PI on 2012-10-06
Anyone have a thought on this: I have a 500GB drive for data, it shows up as /dev/sda in the top right corner of GParted. This is a SATA drive. In the table below under Partition it shows as /dev/sda1 with an error saying superblock problem.

The drive seems to be working fine.  I've looked at it with tune2fs, e2fsck, and fdisk - no problems are indicated.

Here is the main point in GPart the partition is /dev/sda1, none of the other apps can find sda1, they only see sda. 

I'm in over head, but it appears that GParted is trying to read a partition that isn't there, sda1 and giving an error. The entire drive is one partition which I think is sda, which GParted isn't seeing.

Why is GParted getting sda1 rather than sda? In fstab the drives are called by UUID.

I want to add a swap partition to the drive and GParted won't do it, I assume because of the error.

---

### Post by ahallubuntu on 2012-10-06
"sda" isn't a partition, it's the name of the device.

You must have at least one partition on a device to use it, and it would almost certainly be sda1 .  No other program can mount "sda" either, only a partition like "sda1" can be mounted.  Programs that reference disks and not partitions would see "sda" .

Have you tried running e2fsck on /dev/sda1 ?  (Do it while unmounted or you would probably severely corrupt the data.)

What type of partition is this?

Have you checked S.M.A.R.T. status with smartctl or GSmartControl ?

---

### Post by Loki*PI on 2012-10-07
Hi, thanks for reply.  I should do some reading I guess, I thought maybe sda referred to the drive and any partitions would be numerated from that, sda1 etc. 

partition is ext4

I ran e2dsck on /dev/sda1: e2fsck 1.42 (29-Nov-2011)
e2fsck: No such file or directory while trying to open /dev/sda1
Possibly non-existent device?

on sda I get:  sudo e2fsck /dev/sda
e2fsck 1.42 (29-Nov-2011)
500GB: clean, 99560/30531584 files, 41935091/122096646 blocks

SMART is news to me, I'm trying to install GSmartControl, my connection to the net is very slow.  I'll post results a little later.

---

### Post by Loki*PI on 2012-10-07
Have GSmartControl - very cool, thanks.

Ran short test - no errors. Looking through tabs nothing shows an error with the drive. 

Could it be an error in fstab: (below)  the # comments are incorrect / and home are on sdb, a smaller drive.

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f73fdbb1-e1e1-46bc-8d0d-4b3ac28efd7a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=34e13dc7-2775-4b82-8d4e-9d75e3559d5d /home           ext4    defaults        0       2

---

### Post by Loki*PI on 2012-10-11
Anyone have any thoughts on this?

---

### Post by oldfred on 2012-10-11
Try a bit more with e2fsck.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

Post this:

sudo fdisk -lu

If still not working you can try alternative superblock.

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by Loki*PI on 2012-10-12
Hi:  Thanks for the reply, I'll try that.  

Here is output from fdisk -lu    ("invalid partition table" doesn't sound promising.)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000327cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    68356574    34178256   83  Linux
/dev/sdb2        68358144   143859711    37750784   83  Linux
/dev/sdb3       143862075   625137344   240637635   83  Linux

---

### Post by oldfred on 2012-10-12
A few have written data directly to a drive without partitioning. That can be a problem later. 

If you had partitions testdisk may be able to recover them. Testdisk is in the Ubuntu repository or is on most Linux repairCDs.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

