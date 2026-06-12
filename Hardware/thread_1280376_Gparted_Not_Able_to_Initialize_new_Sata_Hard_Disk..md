---
title: "Gparted Not Able to Initialize new Sata Hard Disk."
date: 2009-10-02
forum: Hardware
---

### Post by ryseshan on 2009-10-02
I have Old P4 Machine with only ide connection.  Newly purchased External SATA 250HD. When I try to Format or initialize the following error i get. It completes 100% but give error message as format not able to complete in Windows. Same in Gparted details are posted here.

GParted 0.4.3

Libparted 1.8.8
Format /dev/sdb1 as ext2  00:03:13    ( ERROR )
     	
calibrate /dev/sdb1  00:00:00    ( SUCCESS )
     	
path: /dev/sdb1
start: 63
end: 488392064
size: 488392002 (232.88 GiB)
set partition type on /dev/sdb1  00:00:11    ( SUCCESS )
     	
new partition type: ext2
create new ext2 file system  00:03:01    ( ERROR )
     	
mkfs.ext2 -L "" /dev/sdb1
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
15269888 inodes, 61049000 blocks
3052450 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
1864 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables: done
mke2fs 1.41.4 (27-Jan-2009)
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir

========================================

---

