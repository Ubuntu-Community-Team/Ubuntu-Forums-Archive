---
title: "Short read error when trying to format disk"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by davidsiegel on 2007-07-04
I have a 160 GB Western Digital USB external hard drive. I always get a "short read" error when I try creating a new partition with gparted or fdisk/mkfs. What can I do to fix this error and format the disk?

```

[aesop ~]% sudo mkfs.ext2 /dev/sdg1
mke2fs 1.40-WIP (14-Nov-2006)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
19546112 inodes, 39072080 blocks
1953604 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
1193 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables: done                            
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir

```

The disk was previously formatted as HFS+ and FAT. I simply want to create a single ext2 or ext3 partition on the disk.

---

### Post by davidsiegel on 2007-07-07
So I ran badblocks on the device with:

```
$ badblocks /dev/sdf
```And this reported no bad blocks. What the hell is going on?

---

