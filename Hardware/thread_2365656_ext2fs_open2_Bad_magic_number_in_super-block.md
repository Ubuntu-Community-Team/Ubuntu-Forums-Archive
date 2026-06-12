---
title: "ext2fs_open2: Bad magic number in super-block"
date: 2017-07-09
forum: Hardware
---

### Post by jiapei100 on 2017-07-09
Hi, all:

I'm using Ubuntu 16.04.2 LTS with kernel 4.8.0-58-generic .

And, I've got an external harddrive, and I would like to checkdisk it, so I followed the command lines suggested at [https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/]("https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/"), and did the following with some ERROR info messages:

```
jiapei100@jiapei100-GT72-6QE:~$ sudo fsck.ext4 -v /dev/sdd
e2fsck 1.42.13 (17-May-2015)
ext2fs_open2: Bad magic number in super-block
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sdd

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```

```
jiapei@jiapei-GT72-6QE:~$ sudo mke2fs -n /dev/sdd
mke2fs 1.42.13 (17-May-2015)
Found a dos partition table in /dev/sdd
Proceed anyway? (y,n) y
Creating filesystem with 488378646 4k blocks and 122101760 inodes
Filesystem UUID: d924f8da-b099-4ea8-a1d1-7c91f85521a8
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
        102400000, 214990848
```


Even if I did
```
sudo e2fsck -b 32768 /dev/sdd
```
this issue continues...



Since my external harddrive is newly reformatted, can anybody give me some suggestions, 
**Is my external harddrive broken??? How should I have it repaired?**


Thank you very much
Pei

---

### Post by efflandt on 2017-07-09
You **cannot** e2fsck an entire drive /dev/sdd, so of course you got bad or missing superblock. Try e2fsck for partition(s) on it, like /dev/sdd1, etc., depending upon how many partitions are on it. BTW the -n option for mke2fs does not actually change anything, it just goes through the motions of what it would do. But it recognized that there was an msdos partition on the drive. So what partition(s) display when you do:```
sudo fdisk -l /dev/sdd
```

---

