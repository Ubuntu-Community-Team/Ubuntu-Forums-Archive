---
title: "GParted Live USB error while resizing an ext4 partition"
date: 2016-08-01
forum: Hardware
---

### Post by kroups on 2016-08-01
Hi,

I am trying to resize and move one of my Ubuntu partitions (sda10 for me) so that I can add the unallocated space to another partition (sda9 - to the left from my sda10 partition). I need to do that as I ran out of space on my root partition. I created a GParted live USB, which boots fine. However, an error occurs immediately when I "apply all operations" during resizing the sda10 partition.

Here is the error output:
[HR][/HR]
```
[SIZE=2]GParted 0.26.1 --enable-online-resize

Libparted 3.2

Move /dev/sda10 to the right and shrink it from 170.59 GiB to 150.57 GiB  00:00:13    ( ERROR )
     
calibrate /dev/sda10  00:00:04    ( SUCCESS )
     
path: /dev/sda10 (partition)
start: 558848000
end: 916594687
size: 357746688 (170.59 GiB)
check file system on /dev/sda10 for errors and (if possible) fix them  00:00:06    ( SUCCESS )
     
e2fsck -f -y -v -C 0 /dev/sda10  00:00:06    ( SUCCESS )
     
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure 
Pass 3: Checking directory connectivity 
Pass 4: Checking reference counts
Pass 5: Checking group summary information 

99866 inodes used (0.89%, out of 11182080)
861 non-contiguous files (0.9%)
34 non-contiguous directories (0.0%)
# of inodes with ind/dind/tind blocks: 0/0/0
Extent depth histogram: 99412/58
2214899 blocks used (4.95%, out of 44718336)
0 bad blocks
1 large file

91925 regular files
7540 directories
0 character device files
0 block device files
0 fifos
0 links
392 symbolic links (388 fast symbolic links)
0 sockets
------------
99857 files
e2fsck 1.43.1 (08-Jun-2016)
shrink file system  00:00:03    ( ERROR )
     
resize2fs -p /dev/sda10 157881344K  00:00:03    ( ERROR )
     
Resizing the filesystem on /dev/sda10 to 39470336 (4k) blocks.
Begin pass 3 (max = 1365)
Scanning inode table XXXXXXXXXXXXXXXXXXXXXXXXX---------------
resize2fs 1.43.1 (08-Jun-2016)
========================================[/SIZE]
```

[HR][/HR][SIZE=2][COLOR=#000000]I cannot see the reason for this error and will be grateful for any ideas. Thank you all in advance![/COLOR][/SIZE]

---

### Post by oldfred on 2016-08-01
It says something about 5% used. If so I would just back it up, delete partition and recreate where you want it.

Are you resizing/moving with partitions unmounted from live installer? You cannot have any partitions mounted and even live installer may mount swap, so you have to swap off.
Post this with partition mounted:
df -h

---

### Post by kroups on 2016-08-04
Thank you for your reply. It doesn't seem like it's mounted though.
[ATTACH=CONFIG]270569[/ATTACH]

---

### Post by oldfred on 2016-08-04
All partitions have to be unmounted to resize partitions.
And the live installer normally mounts swap, so make sure that is unmounted also.

To see it in the dh -f command it has to be mounted, but then you need to unmount if you want to resize any partition on sda.

---

