---
title: "Reformat Seagate External 250GB USB drive as ext3"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by tbg58 on 2007-05-27
Had problems with Feisty mounting my external Seagate 250GB USB drive.  I got the answer to mounting it manually here, but I found I couldn't do the thing I had wanted to do, which was to copy my backups of my DVDs here, as the ISO files were larger than 4GB, the max file size for FAT.  Here's a quick and dirty howto on how to format your external drive as an ext3 file system.  Does away with that not-so-Phat 4GB file size limit, and also the need to remember the fancy switches on the mount command:

Do sudo -s (same as su to root).
1.  List the hard drives:
fdisk -l 
You'll see internal drives first.  The external USB drive will come up and list after several seconds due to latency:

root@ubuntu:/# fdisk -l
****(other drives deleted for space)
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    c  W95 FAT32 (LBA)
root@ubuntu:/# 
*** results end ***

Unmount the USB drive if it's mounted.  My mount point was /media/sg
umount /media/sg
(no visible response here - the drive simply unmounts).

Now we want to go into fdisk on the drive.  Remember, the physical drive is (in this example) sdc.  The partition we will be deleting is sdc1, and we will be re-creating the partition and formatting it as ext3.

*** go back into fdisk
We'll go back into fdisk and print the partition table to make sure the partition was deleted:
*** screen from here - comments annotated with asterisks
root@ubuntu:/# fdisk /dev/sdc

The number of cylinders for this disk is set to 30401.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
**** print the partition table
Command (m for help): p

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
**** no partition table listed - that's good.
   Device Boot      Start         End      Blocks   Id  System

**** n command creates a new partition.
Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-30401, default 1): 
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-30401, default 30401): 
Using default value 30401

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
root@ubuntu:/# 
*****

At this point we have a new partition on the disk.  Back at your command prompt do the fdisk -l to list the hard drives:
root@ubuntu:/# fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4862    39053983+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2432    19535008+   7  HPFS/NTFS
/dev/sdb2            2433        4827    19237837+  83  Linux
/dev/sdb3            4828        4863      289170   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   83  Linux
root@ubuntu:/# 
******

We have an unformatted Linux partition on the drive.  Now we just need to format it as ext3.  We do this with the mkfs.ext3 command.  We will use the -b switch to set the block size and in this case I'm using 4096 byte blocks.

root@ubuntu:/# mkfs.ext3 -b 4096 /dev/sdc1
mke2fs 1.40-WIP (14-Nov-2006)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
30539776 inodes, 61049000 blocks
3052450 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
1864 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,         4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 27 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
root@ubuntu:/# 

Once you execute the command, it will begin running.  First the mkfs.ext3 script will write the inode table.  On this drive (250GB) this takes about a minute and a half.
After the inode table is created, the journal will be created quickly, followed by the superblocks and filesystem accounting information.
Creation of the entire file system should take a couple of minutes.

Now you should be able to mount /dev/sdc1 at the directory you create with a simple 
mount /dev/sdc1 /media/sg

And with this you will no longer have the limitations of the FAT (not so Phat) file system.

If you need to write Windows files to this, you have a couple of choices.  You can share it out using Samba or, if your Windows System is the same system, then simply mount your NTFS drive (if your dual boot system is on Feisty 7.04, this should be done for you) and copy over from there to the external drive using your Ubuntu system.  This allows you to do offline backups of your Windows system.

Hope this helps!
Good luck!

---

### Post by spin2cool on 2007-05-28
I prefer to use the live CD with Gparted, which gives you a nice GUI interface to the partitioner.   Also, as an FYI, a little utility called ext2ifs will let you access ext2/3 filesystems from windows.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Ek0nomik on 2007-05-28
You don't have to use the Live CD to use gparted.  You can install gparted on your working Ubuntu.

---

### Post by raintheory on 2007-05-29
Seagate here as well. 250GB

However, not only will the drive not mount as NTFS or HFS+ (tried both), when I boot into windows I get an error saying the drive needs formatted! (I use Macdrive to access HFS+ in Windows).

I replicated this problem 3(!) times. Twice on my laptop and once on my desktop (both feisty).

I formatted the drive as EXT3 and it showed up in Ubuntu, but again when I went into windows with it (using the EXT3 driver as I have done numerous times before with other disks), I get a similar error about the disk and need to reformat.

Frustrating. Luckily I was able to recover the files that were on the disk the first time.

For now I do not trust using the Seagate in Ubuntu.

---

