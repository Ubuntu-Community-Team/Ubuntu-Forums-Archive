---
title: "Grow partition failed, can't access files now..."
date: 2008-09-06
forum: General Help
---

### Post by ethos_dacapo on 2008-09-06
Ok, heres the deal:
I have a 120gb hard drive that had two partitions. One was a 100gb ntfs partition and the other was a 20gb ex3. I was planning on converting the whole drive over to ex3 by converting all the free space to ex3 and then copying the files off of the ntfs partition. Well, to make a long story short it didn't work so instead i tried to grow the partition back to 100% ntfs o the whole drive. This is the error i got:

```
GParted 0.3.5

Libparted 1.7.1

Grow /dev/sdc2 from 94.96 GiB to 114.49 GiB  05:12:43    ( ERROR )
     	
calibrate /dev/sdc2  00:00    ( SUCCES )
     	
path: /dev/sdc2
start: 40965750
end: 240107489
size: 199141740 (94.96 GiB)
calculate new size and position of /dev/sdc2  00:00    ( SUCCES )
     	
requested start: 0
requested end: 240107489
requested size: 240107490 (114.49 GiB)
new start: 63
new end: 240107489
new size: 240107427 (114.49 GiB)
check filesystem on /dev/sdc2 for errors and (if possible) fix them  00:09    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sdc2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sdc2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 101960569344 bytes (101961 MB)
Current device size: 101960570880 bytes (101961 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 83533 MB (81.9%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 87547 MB 0
Multi-Record : 101174 MB 31448
$MFTMirr : 50981 MB 1
Ordinary : 97129 MB 31911
You might resize at 83532726272 bytes or 83533 MB (freeing 18428 MB).
Please make a test run using both the -n and -s options before real resizing!
move partition to the left  00:00    ( SUCCES )
     	
old start: 40965750
old end: 240107489
old size: 199141740 (94.96 GiB)
new start: 63
new end: 199141802
new size: 199141740 (94.96 GiB)
move filesystem to the left  05:12:34    ( SUCCES )
     	
perform readonly test  54:33    ( SUCCES )
     	
using internal algorithm
read 199141740 sectors
finding optimal blocksize
     	
read 32768 sectors using a blocksize of 128 sectors  00:01    ( SUCCES )
     	
32768 of 32768 read
0.565261 seconds
read 32768 sectors using a blocksize of 256 sectors  00:00    ( SUCCES )
     	
32768 of 32768 read
0.571147 seconds
optimal blocksize is 128 sectors (64.00 KiB)
read 199076204 sectors using a blocksize of 128 sectors  54:32    ( SUCCES )
     	
199076204 of 199076204 read
199141740 sectors read
perform real move  04:18:01    ( SUCCES )
     	
using internal algorithm
copy 199141740 sectors
finding optimal blocksize
     	
copy 32768 sectors using a blocksize of 64 sectors  00:02    ( SUCCES )
     	
32768 of 32768 copied
2.11572 seconds
copy 32768 sectors using a blocksize of 128 sectors  00:03    ( SUCCES )
     	
32768 of 32768 copied
2.2181 seconds
optimal blocksize is 64 sectors (32.00 KiB)
copy 199076204 sectors using a blocksize of 64 sectors  04:17:56    ( SUCCES )
     	
199076204 of 199076204 copied
199141740 sectors copied
updating bootsector of ntfs filesystem on /dev/sdc2  00:00    ( SUCCES )
     	
echo 3f000000 | /usr/bin/xxd -r -p | /bin/dd conv=notrunc of=/dev/sdc2 bs=1 seek=28
     	
4+0 records in
4+0 records out
4 bytes (4 B) copied, 7.7655e-05 s, 51.5 kB/s
check filesystem on /dev/sdc2 for errors and (if possible) fix them  00:00    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/sdc2
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Error reading bootsector: Invalid argument.
Failed to startup volume: Invalid argument.
ERROR(22): Opening '/dev/sdc2' as NTFS failed: Invalid argument
The device '/dev/sdc2' doesn't have a valid NTFS.
Maybe you selected the wrong partition? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? This error might also occur
if the disk was incorrectly repartitioned (see the ntfsresize FAQ).
libparted messages    ( INFO )
     	
Error informing the kernel about modifications to partition /dev/sdc2 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sdc2 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sdc (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sdc.

========================================


```

Any ideas? Now both partitions are showing up as ex3 for some reason and when i try to access either partition i get an error. Thanks for your help guys.

```
[74920.822666] EXT3-fs error (device sdc2): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[74920.830770] EXT3-fs: group descriptors corrupted!
[74927.865749] EXT3-fs error (device sdc2): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[74927.873625] EXT3-fs: group descriptors corrupted!
[75870.172599] EXT3-fs error (device sdc2): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[75870.181083] EXT3-fs: group descriptors corrupted!
[77615.018918] EXT3-fs error (device sdc2): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[77615.026777] EXT3-fs: group descriptors corrupted!

```

---

### Post by ethos_dacapo on 2008-09-07
bump...

---

### Post by ethos_dacapo on 2008-09-07
```
sudo fsck /dev/sdc
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

The disk should be ntfs. When i went to resize the partition the first section of the hd was a ex3 but i removed it. The only thing i can figure is since gparted failed its looking for that first partition which was ex3 but now the ntfs is sitting at the front of the disk..... any help would be greatly appreciated i have nearly 100gb of stuff at stake....
How can i get it to look for the correct partition?

```
sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3967e261

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 10.2 GB, 10273920512 bytes
255 heads, 63 sectors/track, 1249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfe7dfe7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1190     9558643+  83  Linux
/dev/sdb2            1191        1249      473917+   5  Extended
/dev/sdb5            1191        1249      473886   82  Linux swap / Solaris

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x006ccccc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *           1       12397    99570870    7  HPFS/NTFS

```

---

### Post by ethos_dacapo on 2008-09-08
Ok folks, i ran testdisk and managed to recover my ntfs partition. The thing is it only works in windows. I think i need to remove all traces of this drive, its portable, from my system so when i plug it in it will be like the first time. I tried it on two systems running ubuntu studio with the latest real time kernel. Any help would be much appreciated and probably time saving. For now i'm going to bed. If anyone else would like to chime in please do so. Thanks

---

### Post by ethos_dacapo on 2008-09-08
one more thing lol 
```
sudo mkdir External_Drive
larry@Studio:/media$ sudo mount /dev/sdc1 /media/External_Drive
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

larry@Studio:/media$ dmesg | tail
[  400.036568] sd 3:0:0:0: [sdc] Write Protect is off
[  400.036576] sd 3:0:0:0: [sdc] Mode Sense: 23 00 00 00
[  400.036579] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  400.036589]  sdc: sdc1
[  400.060478] sd 3:0:0:0: [sdc] Attached SCSI disk
[  400.060528] sd 3:0:0:0: Attached scsi generic sg4 type 0
[  400.622424] EXT3-fs error (device sdc1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[  400.630022] EXT3-fs: group descriptors corrupted!
[ 1090.524674] EXT3-fs error (device sdc1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[ 1090.525674] EXT3-fs: group descriptors corrupted!

```

Its still looking for ex3 how do i correct this? Once again this drive is working in windows fine now so this has to be something in ubuntu needing reconfiged...

---

### Post by ethos_dacapo on 2008-09-08
wow! thanks for all the help guys lol
Since i'm able to access my drive from windoze i'm copying everything to someone elses hard drive who's using xp. Once i get everything off the drive i'll reformat it to ex3 and use the driver from [http://www.fs-driver.org](http://www.fs-driver.org) to copy all my files from ntfs to ex3 in xp. I'll ley everyone know how it goes for those who may read this post in the future and need to know if everything works.

---

