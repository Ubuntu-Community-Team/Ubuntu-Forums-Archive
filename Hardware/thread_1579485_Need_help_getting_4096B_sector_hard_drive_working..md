---
title: "Need help getting 4096B sector hard drive working."
date: 2010-09-21
forum: Hardware
---

### Post by CraigFoote on 2010-09-21
I just bought one of those Western Digital 1TB drives with the 4096B sectors that are reported as 512B and I need some help getting it to work right. I tried following the thread at [http://ubuntuforums.org/showthread.php?t=1407098](http://ubuntuforums.org/showthread.php?t=1407098) but I'm obviously doing something wrong. I tried using GParted but it seemed to use 512B sectors which the post above said was wrong. It also started the first sector at 63B and I think it's supposed to be 64B.

Any help greatly appreciated.

$ sudo fdisk -u -c -b 4096 /dev/sdd
Note: sector size is 4096 (not 512)

Command (m for help): n
Command action
e extended
p primary partition (1-4)
p
Partition number (1-4): 1
First sector (256-244178943, default 256): [I pressed Enter for default]
Using default value 256
Last sector, +sectors or +size{K,M,G} (256-244178943, default 244178943): [I pressed Enter for default]
Using default value 244178943

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

$ sudo mkfs.ext4 -b 4096 -L "External-HD" -O extent -v /dev/sdd
mke2fs 1.41.11 (14-Mar-2010)
/dev/sdd is entire device, not just one partition!
Proceed anyway? (y,n) y
fs_types for mke2fs.conf resolution: 'ext4', 'default'
Calling BLKDISCARD from 0 to 1000156954624 failed.
Filesystem label=External-HD
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
61046784 inodes, 244178944 blocks
12208947 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
7452 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done :)

This filesystem will be automatically checked every 37 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

$ sudo fdisk -l /dev/sdd

Disk /dev/sdd: 1000.2 GB, 1000156954624 bytes
255 heads, 63 sectors/track, 121595 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes :confused:
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table :confused:

$ sudo mkdir /media/External-HD
$ sudo mount -t ext4 /dev/sdd /media/External-HD
$ sudo ls -al /media
...
drwxr-xr-x	3	root	root	4096	2010-09-21 22:08	External-HD
...

$ sudo chmod -Rv 777 /media/External-HD/
$ sudo ls -al /media
...
drwxrwxrwx	3	root	root	4096	2010-09-21 22:08	External-HD
...

At this point I copied a text file in nautilus and pasted into the mounted folder. I then opened the file from the mounted folder and it opened ok. :)

I then opened GParted and it displayed warnings about /dev/sdd:
[quote]
File system: ext4
Size: 931.47GB
Flags:
Status: Not mounted :confused:
Label: :confused:
UUID:
First sector: 0 :confused:
Last sector: 195341551
Total sectors: 195341552
Warning:
e2label: Bad magic number in super-block while trying to open /dev/sdd1
Coundn't find valid filesystem superblock while trying to open /dev/sdd1

Unable to read the content of this file system!
Because of this some operations may be unavilable.
[unquote]
:confused:

Well it seems to work but I can't trust it with all those errors. What am I doing wrong?

Craig

---

### Post by srs5694 on 2010-09-21
> **CraigFoote said:**
> I just bought one of those Western Digital 1TB drives with the 4096B sectors that are reported as 512B and I need some help getting it to work right. I tried following the thread at [http://ubuntuforums.org/showthread.php?t=1407098](http://ubuntuforums.org/showthread.php?t=1407098) but I'm obviously doing something wrong. I tried using GParted but it seemed to use 512B sectors which the post above said was wrong. It also started the first sector at 63B and I think it's supposed to be 64B.

I'm not sure what you mean by "the post above" -- that thread has 30 posts in it!

I recommend you read [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) I wrote for IBM developerWorks. Although the main thrust of the article is presenting experimental evidence about the performance penalty of getting the partitioning wrong, the "Aligning Partitions" section offers practical partitioning advice. Note, however, that some newer versions of partitioning tools have changed for the better since I wrote that article. In particular, the latest versions of GParted can now do proper alignment quite easily. (I don't recall offhand what's used in various versions of Ubuntu, though.)

> Well it seems to work but I can't trust it with all those errors. What am I doing wrong?

You're overthinking it. As far as Linux is concerned, the drive has 512-byte sectors. You should *not* tell partitioning tools otherwise, as you did. You *should,* however, take whatever measures are necessary to get the partitions to start on 8-sector boundaries. Using the "-u -c" option to fdisk (but [i]not[/] "-b 4096") will do this with recent versions, at least for the first partition. If you care to use GPT rather than MBR partitions, you could use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) version 0.6.6 or later (I recommend the latest, version 0.6.10); it aligns all partitions on 2048-sector boundaries by default, at least when you start with a blank disk.

No matter how you do it, you definitely should *not* see the sort of error messages shown in your quoted session.

---

