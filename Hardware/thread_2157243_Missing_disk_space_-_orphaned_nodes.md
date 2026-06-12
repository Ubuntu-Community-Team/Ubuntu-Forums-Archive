---
title: "Missing disk space - orphaned nodes?"
date: 2013-06-24
forum: Hardware
---

### Post by AlistairSellar on 2013-06-24
Hi,

I am short of space in / and df suggests there is space missing (the "Avail" on / does not equal the difference between "Size" and "Used"):
```

$ df
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       6.5G  5.8G  350M  95% /
udev            744M  4.0K  744M   1% /dev
tmpfs           301M  788K  300M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            751M   76K  751M   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sda5        11G  4.9G  4.8G  51% /home

```

I wonder if the difference of ~400M is due to orphaned nodes?  

```
$ sudo fsck -fn /dev/sda2
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
Warning!  /dev/sda2 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 91101 has zero dtime.  Fix? no


Inodes that were part of a corrupted orphan linked list found.  Fix? no


Inode 91233 was part of the orphaned inode list.  IGNORED.
Inode 91663 was part of the orphaned inode list.  IGNORED.
Inode 149081 was part of the orphaned inode list.  IGNORED.
Inode 149180 was part of the orphaned inode list.  IGNORED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(372747--372748) -(372927--372929) -(372957--372961) -(389486--389487) -389496 -620472 -620481
Fix? no


Free blocks count wrong for group #11 (18436, counted=18435).
Fix? no


Free blocks count wrong for group #18 (1698, counted=1696).
Fix? no


Free blocks count wrong (174933, counted=174861).
Fix? no


Inode bitmap differences:  -91101 -91233 -91663 -91677 -149081 -149180
Fix? no


Free inodes count wrong for group #11 (2, counted=1).
Fix? no


Free inodes count wrong for group #18 (3508, counted=3506).
Fix? no


Free inodes count wrong (86878, counted=86863).
Fix? no




/dev/sda2: ********** WARNING: Filesystem still has errors **********


/dev/sda2: 340514/427392 files (0.8% non-contiguous), 1534051/1708984 blocks

```

Any suggestions welcome, but please note I'm not an expert so don't want to take any risks with the filesystem.

Thanks,
Alistair

---

### Post by steeldriver on 2013-06-24
If you're concerned about inode usage, you can use df with the '-i' switch e.g.

```
 df -hi
```

however I think that your ~400MB discrepancy is likely just because the ext2/3/4 filesystems reserve a certain number of blocks (default is 5% iirc) for system overhead i.e.

6.5G - 5% = 6.175G

6.175G - 5.8G (used) = 0.375G free

You can use tune2fs to see what reserved fraction you have e.g.

```
sudo tune2fs -l /dev/sda2
```

---

