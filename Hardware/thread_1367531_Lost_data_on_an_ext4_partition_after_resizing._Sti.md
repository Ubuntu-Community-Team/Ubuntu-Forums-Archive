---
title: "Lost data on an ext4 partition after resizing. Still have hope and time.e2fsck."
date: 2009-12-29
forum: Hardware
---

### Post by damianusthesage on 2009-12-29
As my /home began to push the size of my / directory beyond reasonable levels ( " This partition has 64kb available" ), I thanked myself that I was even able to log in and set about resizing my partitions.

Everything was going on as usual and at the same interminably slow rate, so I left the machine working away copying data from one spot to another, and went to enjoy the West Wing box set that I had recently started.

On returning to my machine, I found that gparted had completed, except with an error. i saved the .htm - suffixed log file.

I have now burnt the ultimate boot disc and the system rescue disk, but have no idea where to start.

Can anyone point me to a decent how-to or give me some bullet points. I am an experienced Linux user, hoping to avoid mistakes, so you needn't do much more than this.

You'll be glad to hear I've already bought 2 usb hard drives for back up in future, to avoid this kind of foolishness.

The GParted log that was produced looks like this:

GParted 0.4.5

Libparted 1.8.8.1.159-1e0e

Delete Logical Partition (unknown, 1.40 GiB) from /dev/sda  00:00:02    ( SUCCESS )
    	
calibrate /dev/sda6  00:00:01    ( SUCCESS )
    	
path: /dev/sda6
start: 231502383
end: 234435599
size: 2933217 (1.40 GiB)
delete partition  00:00:01    ( SUCCESS )
========================================

Move /dev/sda5 to the left and grow it from 39.05 GiB to 40.45 GiB  01:20:12    ( ERROR )
    	
calibrate /dev/sda5  00:00:01    ( SUCCESS )
    	
path: /dev/sda5
start: 149612400
end: 231502319
size: 81889920 (39.05 GiB)
calculate new size and position of /dev/sda5  00:00:00    ( SUCCESS )
    	
requested start: 149597343
requested end: 234436544
requested size: 84839202 (40.45 GiB)
new start: 149597280
new end: 234420479
new size: 84823200 (40.45 GiB)
check file system on /dev/sda5 for errors and (if possible) fix them  00:00:02    ( SUCCESS )
    	
e2fsck -f -y -v /dev/sda5
    	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

11 inodes used (0.00%)
0 non-contiguous files (0.0%)
0 non-contiguous directories (0.0%)
# of inodes with ind/dind/tind blocks: 0/0/0
Extent depth histogram: 1
205643 blocks used (2.01%)
0 bad blocks
1 large file

0 regular files
2 directories
0 character device files
0 block device files
0 fifos
0 links
0 symbolic links (0 fast symbolic links)
0 sockets
--------
2 files
e2fsck 1.41.9 (22-Aug-2009)
move partition to the left  00:00:01    ( SUCCESS )
    	
old start: 149612400
old end: 231502319
old size: 81889920 (39.05 GiB)
new start: 149597280
new end: 231487199
new size: 81889920 (39.05 GiB)
move file system to the left  01:19:59    ( SUCCESS )
    	
perform read-only test  00:24:50    ( SUCCESS )
    	
using internal algorithm
read 81889920 sectors
finding optimal blocksize
    	
read 65536 sectors using a blocksize of 128 sectors  00:00:03    ( SUCCESS )
    	
65536 of 65536 read
2.20077 seconds
read 65536 sectors using a blocksize of 256 sectors  00:00:01    ( SUCCESS )
    	
65536 of 65536 read
1.49502 seconds
read 65536 sectors using a blocksize of 512 sectors  00:00:02    ( SUCCESS )
    	
65536 of 65536 read
1.44045 seconds
read 65536 sectors using a blocksize of 1024 sectors  00:00:01    ( SUCCESS )
    	
65536 of 65536 read
1.44315 seconds
read 65536 sectors using a blocksize of 2048 sectors  00:00:01    ( SUCCESS )
    	
65536 of 65536 read
1.33308 seconds
read 65536 sectors using a blocksize of 4096 sectors  00:00:02    ( SUCCESS )
    	
65536 of 65536 read
1.72031 seconds
read 65536 sectors using a blocksize of 8192 sectors  00:00:02    ( SUCCESS )
    	
65536 of 65536 read
1.69965 seconds
read 65536 sectors using a blocksize of 16384 sectors  00:00:01    ( SUCCESS )
    	
65536 of 65536 read
1.63757 seconds
read 65536 sectors using a blocksize of 32768 sectors  00:00:02    ( SUCCESS )
    	
65536 of 65536 read
1.5538 seconds
read 65536 sectors using a blocksize of 65536 sectors  00:00:01    ( SUCCESS )
    	
65536 of 65536 read
1.45068 seconds
optimal blocksize is 2048 sectors (1.00 MiB)    ( ERROR )
read 81234560 sectors using a blocksize of 2048 sectors  00:24:34    ( SUCCESS )
    	
81234560 of 81234560 read
81889920 sectors read
perform real move  00:55:09    ( SUCCESS )
    	
using internal algorithm
copy 81889920 sectors
finding optimal blocksize
    	
copy 65536 sectors using a blocksize of 64 sectors  00:00:03    ( SUCCESS )
    	
65536 of 65536 copied
2.89631 seconds
copy 65536 sectors using a blocksize of 128 sectors  00:00:03    ( SUCCESS )
    	
65536 of 65536 copied
2.69941 seconds
copy 65536 sectors using a blocksize of 256 sectors  00:00:02    ( SUCCESS )
    	
65536 of 65536 copied
2.85507 seconds
copy 65536 sectors using a blocksize of 512 sectors  00:00:03    ( SUCCESS )
    	
65536 of 65536 copied
2.42499 seconds
copy 65536 sectors using a blocksize of 1024 sectors  00:00:03    ( SUCCESS )
    	
65536 of 65536 copied
2.75608 seconds
copy 65536 sectors using a blocksize of 2048 sectors  00:00:02    ( SUCCESS )
    	
65536 of 65536 copied
2.62346 seconds
copy 65536 sectors using a blocksize of 4096 sectors  00:00:03    ( SUCCESS )
    	
65536 of 65536 copied
2.53717 seconds
copy 65536 sectors using a blocksize of 8192 sectors  00:00:03    ( SUCCESS )
    	
65536 of 65536 copied
2.91325 seconds
copy 65536 sectors using a blocksize of 16384 sectors  00:00:03    ( SUCCESS )
    	
65536 of 65536 copied
2.87089 seconds
copy 65536 sectors using a blocksize of 32768 sectors  00:00:03    ( SUCCESS )
    	
65536 of 65536 copied
2.97319 seconds
copy 65536 sectors using a blocksize of 65536 sectors  00:00:02    ( SUCCESS )
    	
65536 of 65536 copied
2.81313 seconds
optimal blocksize is 512 sectors (256.00 KiB)
copy 81169024 sectors using a blocksize of 512 sectors  00:54:39    ( SUCCESS )
    	
81169024 of 81169024 copied
81889920 sectors copied
check file system on /dev/sda5 for errors and (if possible) fix them  00:00:04    ( SUCCESS )
    	
e2fsck -f -y -v /dev/sda5
    	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

11 inodes used (0.00%)
0 non-contiguous files (0.0%)
0 non-contiguous directories (0.0%)
# of inodes with ind/dind/tind blocks: 0/0/0
Extent depth histogram: 1
205643 blocks used (2.01%)
0 bad blocks
1 large file

0 regular files
2 directories
0 character device files
0 block device files
0 fifos
0 links
0 symbolic links (0 fast symbolic links)
0 sockets
--------
2 files
e2fsck 1.41.9 (22-Aug-2009)
grow file system to fill the partition  00:00:00    ( SUCCESS )
    	
resize2fs /dev/sda5
    	
resize2fs 1.41.9 (22-Aug-2009)
The filesystem is already 10236240 blocks long. Nothing to do!

calculate new size and position of /dev/sda5  00:00:01    ( SUCCESS )
    	
requested start: 149597280
requested end: 234420479
requested size: 84823200 (40.45 GiB)
new start: 149597280
new end: 234420479
new size: 84823200 (40.45 GiB)
check file system on /dev/sda5 for errors and (if possible) fix them  00:00:02    ( SUCCESS )
    	
e2fsck -f -y -v /dev/sda5
    	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

11 inodes used (0.00%)
0 non-contiguous files (0.0%)
0 non-contiguous directories (0.0%)
# of inodes with ind/dind/tind blocks: 0/0/0
Extent depth histogram: 1
205643 blocks used (2.01%)
0 bad blocks
1 large file

0 regular files
2 directories
0 character device files
0 block device files
0 fifos
0 links
0 symbolic links (0 fast symbolic links)
0 sockets
--------
2 files
e2fsck 1.41.9 (22-Aug-2009)
grow partition from 39.05 GiB to 40.45 GiB  00:00:02    ( SUCCESS )
    	
old start: 149597280
old end: 231487199
old size: 81889920 (39.05 GiB)
new start: 149597280
new end: 234420479
new size: 84823200 (40.45 GiB)
check file system on /dev/sda5 for errors and (if possible) fix them  00:00:00    ( ERROR )
    	
e2fsck -f -y -v /dev/sda5
    	

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device&gt;

e2fsck 1.41.9 (22-Aug-2009)
e2fsck: No such file or directory while trying to open /dev/sda5 
grow file system to fill the partition  00:00:00    ( ERROR )
    	
resize2fs /dev/sda5
    	
resize2fs 1.41.9 (22-Aug-2009)
open: No such file or directory while opening /dev/sda5 
libparted messages    ( INFO )
    	
Error informing the kernel about modifications to partition /dev/sda5 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda5 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sda (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sda.
========================================

Shrink /dev/sda5 from 40.45 GiB to 39.48 GiB
========================================

Create Logical Partition #1 (linux-swap, 996.19 MiB) on /dev/sda
========================================

Set Partition Label "Virtual" on /dev/sda5
========================================

Set Partition Label "Files" on /dev/sda6
========================================

Set Partition Label "Backup" on /dev/sda2
========================================

Create Primary Partition #2 (ext2, 7.84 MiB) on /dev/sda
========================================

---

