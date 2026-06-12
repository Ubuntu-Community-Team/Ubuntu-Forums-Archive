---
title: "Trouble writing superblocks"
date: 2018-09-12
forum: Hardware
---

### Post by bananskall on 2018-09-12
Trying to create partitions on a 500 GB disk model WD AV-25.

Disk is connected with SATA plug.

It shows up in KDE Partition manager, but attempting to create partitions gives an uninformative error:
```
Create a new partition table (type: gpt) on ‘/dev/sdb’ 
Job: Create new partition table on device ‘/dev/sdb’ 
Create new partition table on device ‘/dev/sdb’: Error
Create a new partition table (type: gpt) on ‘/dev/sdb’: Error
```
Importantly, and differing from other posts i see about this problem, is that when i run all three types of SMART tests (also the one taking over an hour) they report everything working 100% and a long lifespan remaining.

When running:
```
sudo mkfs -t ext4 /dev/sdb

```
It gives the following errors:
```
mke2fs 1.42.13 (17-May-2015)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
Warning: could not erase sector 2: Attempt to write block to filesystem resulted in short write
Creating filesystem with 122096646 4k blocks and 30531584 inodes
Filesystem UUID: bd6a761a-cd06-4a97-9acf-6aca0a47522f
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
        102400000

Allocating group tables: done                            
Warning: could not read block 0: Attempt to read block from filesystem resulted in short read
Warning: could not erase sector 0: Attempt to write block to filesystem resulted in short write
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information:    0/3727
```

This WD AV-25 disk is extracted from a set-top box. Similar disks from identically looking boxes have worked before.

Any ideas?

---

