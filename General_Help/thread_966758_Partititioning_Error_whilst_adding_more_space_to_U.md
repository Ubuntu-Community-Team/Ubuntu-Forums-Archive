---
title: "Partititioning Error whilst adding more space to Ubuntu"
date: 2008-11-01
forum: General Help
---

### Post by Glubbdubdribian on 2008-11-01
Hi, I was trying to add more space to my Ubuntu partition from the partition i use for Windows Vista but there was an error in gpart. Here is my fdisk -l config:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f97e765

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2              15        1320    10485760   83  Linux
/dev/sda3   *        1320        7466    49367745    7  HPFS/NTFS
/dev/sda4            9460        9729     2168775   82  Linux swap / Solaris

```

I created 15 gigs of free space after sda3 but then, when i try to move the free space to the start of sda3 (i.e. shifting my windows partition to the right, i think), there is an error.

Here are the error details:

```
GParted 0.3.5

Libparted 1.7.1

Move /dev/sda3 to the right  04:39    ( ERROR )
     	
calibrate /dev/sda3  00:01    ( SUCCES )
     	
path: /dev/sda3
start: 21196800
end: 119932289
size: 98735490 (47.08 GiB)
calculate new size and position of /dev/sda3  00:00    ( SUCCES )
     	
requested start: 53223345
requested end: 151958834
requested size: 98735490 (47.08 GiB)
new start: 53223345
new end: 151958834
new size: 98735490 (47.08 GiB)
check filesystem on /dev/sda3 for errors and (if possible) fix them  00:03    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda3
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda3
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 50552566272 bytes (50553 MB)
Current device size: 50552570880 bytes (50553 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 16709 MB (33.1%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 3275 MB 0
Multi-Record : 36051 MB 35080
$MFTMirr : 34587 MB 1
Compressed : 36049 MB 12772
Sparse : 36053 MB 36037
Ordinary : 39098 MB 55565
You might resize at 16708059136 bytes or 16709 MB (freeing 33844 MB).
Please make a test run using both the -n and -s options before real resizing!
move filesystem to the right  04:35    ( ERROR )
     	
perform readonly test  04:35    ( ERROR )
     	
using internal algorithm
read 98735490 sectors
finding optimal blocksize
     	
read 32768 sectors using a blocksize of 128 sectors  00:02    ( SUCCES )
     	
32768 of 32768 read
1.27658 seconds
read 32768 sectors using a blocksize of 256 sectors  00:01    ( SUCCES )
     	
32768 of 32768 read
1.05204 seconds
read 32768 sectors using a blocksize of 512 sectors  00:01    ( SUCCES )
     	
32768 of 32768 read
0.969617 seconds
read 32768 sectors using a blocksize of 1024 sectors  00:00    ( SUCCES )
     	
32768 of 32768 read
0.718197 seconds
read 32768 sectors using a blocksize of 2048 sectors  00:01    ( SUCCES )
     	
32768 of 32768 read
0.880776 seconds
optimal blocksize is 1024 sectors (512.00 KiB)
read 98571650 sectors using a blocksize of 1024 sectors  04:30    ( ERROR )
     	
11793794 of 98571650 read
Error while reading block at sector 107973632
11957634 sectors read
libparted messages    ( INFO )
     	
Input/output error during read on /dev/sda
```

Could anyone please help? Is there anyway for me to move the space onto my Ubuntu partition? thanks in advance :)

---

### Post by Glubbdubdribian on 2008-11-01
bump.

does anybody have any ideas please? thx :)

---

### Post by Glubbdubdribian on 2008-11-10
yeah.. this is no longer an issue; I destroyed both my ubuntu and vista partition so I'm just going to reinstall.

---

