---
title: "WD 3TB drive mounts as 2TB drive"
date: 2016-01-23
forum: Hardware
---

### Post by pete46 on 2016-01-23
Hi, I've tried to add another drive into my media drive, but it's not behaving.
[B]
When I mount the drive, fdisk reports it as 2.7TB:[/B]

*Disk /dev/sde: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 4096 bytes*
*I/O size (minimum/optimal): 4096 bytes / 4096 bytes*
*Disklabel type: gpt*
*Disk identifier: 95B88D0E-9D99-40E1-AC7B-CD5B00F83FB6*

*Device     Start        End    Sectors  Size Type*
*/dev/sde1   2048 5860533134 5860531087  2.7T Linux filesystem*


[B]However when I run 'df -h', it reports it as 2.0TB:
[/B]

*/dev/sde1       2.0T   71M  1.9T   1% /media/hd3c*

Where has my other 0.7TB gone and how do I get it back?

I tried deleting the partition and creating a new one, but the same thing always happens. 

I should say that I tried setting this drive up a few months back and messed something up but can't remember exactly what...!

Any thoughts?

Cheers

Pete

---

### Post by sq7bti on 2016-01-23
[https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits](https://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits)

---

### Post by pete46 on 2016-01-24
Thanks, but I believe the drive is ext4:

/dev/sde1: Linux rev 1.0 ext4 filesystem data, UUID=6626fa67-f749-41b7-9239-289bdf02f2f8 (needs journal recovery) (extents) (large files) (huge files)

That link says the max volume size on ext4 is 1 EiB

---

### Post by oldfred on 2016-01-24
Post this to see if it says any errors:
 sudo gdisk -l /dev/sde

---

### Post by pete46 on 2016-01-24
Is gdisk a thing I've not heard of or a typo for fdisk?

If the latter, then it gives the rather vague...

pete@media:~$ sudo fdisk -l /dev/sde
fdisk: cannot open /dev/sde: Input/output error

---

### Post by oldfred on 2016-01-24
Gdisk is the fdisk for gpt partitioned drives. Fdisk currently does not support gpt, new version in 16.04 will.

 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by ajgreeny on 2016-01-24
No gdisk is the command needed for disks using GPT partition tables, which yours probably should be using.
Your fdisk command should give an error output similar to mine below if using GPT partition table, and GPT partition table is needed for partitions above 2TB if that is what you really want on your 3TB disk.

Your fdisk output does show a partition of 2TB and also a disk label ```
Disklabel type: gpt
``` but I think the disk label is not actually telling the truth and that you have an msdos partition table.
My fdisk output on a GPT partitioned disk shows
```
sudo fdisk -l /dev/sda
[sudo] password for ajgreeny: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.
```

You should be able to either make a second partition on that 3TB disk to use the space that is now "missing", ie unallocated, or if you insist on a single 3TB partition you will have to make a new GPT partition table.

---

### Post by pete46 on 2016-01-24
Thanks. I checked if i could create another partition on the drive but it said 'no sector available' or similar.

Installed gdisk and created a new empty partition table and then a new partition.

**sudo gdisk -l /dev/sde** now gives:


*GPT fdisk (gdisk) version 0.8.1*
[I]
[/I]
*Partition table scan:*
*  MBR: protective*
*  BSD: not present*
*  APM: not present*
*  GPT: present*
[I]
[/I]
*Found valid GPT with protective MBR; using GPT.*
*Disk /dev/sde: 5860533168 sectors, 2.7 TiB*
*Logical sector size: 512 bytes*
*Disk identifier (GUID): B802942A-EAA8-4BA5-86B6-76BD70E3A4E9*
*Partition table holds up to 128 entries*
*First usable sector is 34, last usable sector is 5860533134*
*Partitions will be aligned on 2048-sector boundaries*
*Total free space is 2014 sectors (1007.0 KiB)*
[I]
[/I]
*Number  Start (sector)    End (sector)  Size       Code  Name*
*   1            2048      5860533134   2.7 TiB     8300  Linux filesystem*


**fdisk -l** gives a long pause before it gets to /dev/sde and then gives:



*Disk /dev/sde: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors*
*Units: sectors of 1 * 512 = 512 bytes*
*Sector size (logical/physical): 512 bytes / 4096 bytes*
*I/O size (minimum/optimal): 4096 bytes / 4096 bytes*
*Disklabel type: gpt*
*Disk identifier: B802942A-EAA8-4BA5-86B6-76BD70E3A4E9*
[I]
[/I]
*Device     Start        End    Sectors  Size Type*
**
*/dev/sde1   2048 5860533134 5860531087  2.7T Linux filesystem*


However, the real problem is that I don't seem able to mount it:

pete@media:~$ **sudo mount /dev/sde1 /media/hd3c/**
*mount: wrong fs type, bad option, bad superblock on /dev/sde1,*
*       missing codepage or helper program, or other error*
[I]
[/I]
*       In some cases useful info is found in syslog - try*
*       dmesg | tail or so.*




**dmesg | tail **then gives:

*[ 1764.186392] Sense Key : Medium Error [current] [descriptor]*
*[ 1764.186398] Descriptor sense data with sense descriptors (in hex):*
*[ 1764.186402]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 *
*[ 1764.186419]         7f c4 08 18 *
*[ 1764.186428] sd 3:0:0:0: [sde]  *
*[ 1764.186433] Add. Sense: Unrecovered read error - auto reallocate failed*
*[ 1764.186438] sd 3:0:0:0: [sde] CDB: *
*[ 1764.186441] Read(16): 88 00 00 00 00 00 7f c4 08 18 00 00 00 f0 00 00*
*[ 1764.186461] end_request: I/O error, dev sde, sector 2143553560*
*[ 1764.186525] ata4: EH complete*

---

### Post by oldfred on 2016-01-24
Did you create a /media/hd3c as a mount point?
Have you tried fsck?

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sde1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sde1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sde1

Also some external drive caddies do not support USB3 or do not support gpt or drives over 2TiB. Since shown correctly above with gdisk, yours probably does.

---

### Post by pete46 on 2016-01-24
Thanks, yes I created the mounting point. And it's an internal drive rather than a caddy.

**sudo e2fsck -C0 -p -f -v /dev/sde1** gave:

*Error reading block 3145728 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps.  *

*/dev/sde1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.*
*	(i.e., without -a or -p options)*

[B]
sudo e2fsck -f -y -v /dev/sde1[/B] gave:


*e2fsck 1.42.10 (18-May-2014)**Pass 1: Checking inodes, blocks, and sizes*
*Pass 2: Checking directory structure*
*Pass 3: Checking directory connectivity*
*Pass 4: Checking reference counts*
*Pass 5: Checking group summary information*
*Error reading block 3145728 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps.  Ignore error? yes*
*Force rewrite? yes*

It then repeated those last two lines for a hundred or so different blocks before moving onto many lines of this sort of thing:


*Block bitmap differences:  +3145728 +3145744 +(3145760--3146271) +7340032 +7340048 +(7340064--7340575) +7864320 +7864336 +(7864352--7864863) +8388608 +8388624 +(8388640--8389151) *


Before ending with:

Fix? yes


[I]
[/I]
*/dev/sde1: ***** FILE SYSTEM WAS MODIFIED ******
[I]
[/I]
*          11 inodes used (0.00%, out of 134217728)*
*           0 non-contiguous files (0.0%)*
*           0 non-contiguous directories (0.0%)*
*             # of inodes with ind/dind/tind blocks: 0/0/0*
*             Extent depth histogram: 3*
*     8474650 blocks used (1.58%, out of 536870655)*
*           0 bad blocks*
*           1 large file*
[I]
[/I]
*           0 regular files*
*           2 directories*
*           0 character device files*
*           0 block device files*
*           0 fifos*
*           0 links*
*           0 symbolic links (0 fast symbolic links)*
*           0 sockets*
*------------*
*           2 files*


Running** gdisk** after then gave:
[I]
Warning! Read error 5; strange behavior now likely![/I]
[I]Warning! Read error 5; strange behavior now likely!

[/I]
The partition I'd created was gone so I created another. Then **mount**ing gave:


[I]mount: /dev/sde1: can't read superblock


[/I]I tried fsck again to see if it would complain about the same errors, but it gave


*e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sde1**Could this be a zero-length partition?*

---

### Post by oldfred on 2016-01-24
You could try a backup superblock.
But I do not think a new drive should be giving these errors.
What system, And do you have AHCI on in BIOS, not IDE nor RAID?

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

