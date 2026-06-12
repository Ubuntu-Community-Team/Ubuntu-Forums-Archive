---
title: "Bad magic number in super-block"
date: 2024-10-26
forum: Hardware
---

### Post by peyre on 2024-10-26
I'm running Xubuntu 24.04 on a 512GB SSD (ext4) and am not experiencing issues, except I checked dmesg the other day and it returned errors like these:

```
[ 2545.428343] sd 7:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK cmd_age=0s
[ 2545.428366] sd 7:0:0:0: [sdd] tag#0 Sense Key : Medium Error [current] 
[ 2545.428376] sd 7:0:0:0: [sdd] tag#0 Add. Sense: Unrecovered read error
[ 2545.428387] sd 7:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 00 04 00 00 01 00 00 00
[ 2545.428393] critical medium error, dev sdd, sector 4 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 2545.428453] FAT-fs (sdd): FAT read failed (blocknr 4)
[ 2546.228250] sd 7:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK cmd_age=0s
[ 2546.228274] sd 7:0:0:0: [sdd] tag#0 Sense Key : Medium Error [current] 
[ 2546.228284] sd 7:0:0:0: [sdd] tag#0 Add. Sense: Unrecovered read error
[ 2546.228294] sd 7:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 00 04 00 00 04 00 00 00
[ 2546.228301] critical medium error, dev sdd, sector 4 op 0x0:(READ) flags 0x80700 phys_seg 4 prio class 0
[ 2547.028177] sd 7:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK cmd_age=0s
[ 2547.028201] sd 7:0:0:0: [sdd] tag#0 Sense Key : Medium Error [current] 
[ 2547.028211] sd 7:0:0:0: [sdd] tag#0 Add. Sense: Unrecovered read error
[ 2547.028259] sd 7:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 00 00 00 04 00 00 01 00 00 00
[ 2547.028268] critical medium error, dev sdd, sector 4 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[ 2547.028332] FAT-fs (sdd): FAT read failed (blocknr 4)
```

So this morning I fired the system up with a live disk, and ran sudo fsck -y /dev/sda, and it returned this sort of thing:
```
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck-ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem. If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
  e2fsck -b 8193 <device>
of
  e2fsck -b 32768 <device>

Found a gpt partition table in /dev/sda
```

Running **e2fsck -b 8193 /dev/sda** or the same for **32768** returns:
```
e2fsck: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem. If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
  e2fsck -b 8193 <device>
of
  e2fsck -b 32768 <device>

Found a gpt partition table in /dev/sda
```

---

### Post by tea for one on 2024-10-26
> **peyre said:**
> 
So this morning I fired the system up with a live disk, and ran sudo fsck -y /dev/sda, and it returned this sort of thing:
You should run fsck on a partition not the disk
```
sudo fsck /dev/sda1
```
```
sudo fsck /dev/sda2
```

---

### Post by peyre on 2024-10-26
Ha!  That simple, eh?  I'll reboot and try it.

---

### Post by peyre on 2024-10-26
That definitely changed things.  I have the default partitioning for Xubuntu, so my system is on sda3.  Running sudo fsck -y /dev/sda3 returns:

```
fsck from util-linux 2.39.3
e2fsck 1.47.0 (5-Feb-2023)
/dev/sda3: clean, 637041/31227904 files, 57322824/124894976 blocks
```

Now it returned this immediately, so I image it wasn't really checking the file system thoroughly.  Is/are there different switches I should be using?

---

### Post by Rubi1200 on 2024-10-27
You could try this:

```
sudo e2fsck -C0 -p -f -v /dev/sda3

```

Make sure partitions are unmounted and change sda3 to whatever if needed.

The command will force a full check and fix minor errors as well as displaying the progress and output in the terminal.

---

### Post by peyre on 2024-10-27
Thanks!  Here's the result.  Looks like I'm probably ok?

```
/dev/sda3:                                                                      Inode 17302118 extent tree (at level 1) could be shorter.  IGNORED.
/dev/sda3: Inode 17317590 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 17318374 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 17319905 extent tree (at level 1) could be narrower.  IGNORED.
/dev/sda3: Inode 17320072 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 17320078 extent tree (at level 1) could be narrower.  IGNORED.
/dev/sda3: Inode 17323842 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 17325453 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 17325519 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3:                                                                      Inode 18612232 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 18615704 extent tree (at level 1) could be narrower.  IGNORED.
/dev/sda3: Inode 18618960 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 18619002 extent tree (at level 1) could be narrower.  IGNORED.
/dev/sda3: Inode 18630212 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 18630314 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 18633434 extent tree (at level 1) could be narrower.  IGNORED.
/dev/sda3: Inode 18633439 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3:                                                                      Inode 19935305 extent tree (at level 1) could be narrower.  IGNORED.
/dev/sda3: Inode 19951336 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 19951639 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3:                                                                      Inode 21899432 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 21901218 extent tree (at level 2) could be narrower.  IGNORED.
                                                                               
      637361 inodes used (2.04%, out of 31227904)
        7180 non-contiguous files (1.1%)
         763 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 609158/703/15
    59366366 blocks used (47.53%, out of 124894976)
           0 bad blocks
          21 large files

      539383 regular files
       68481 directories
           8 character device files
           0 block device files
           1 fifo
          75 links
       29478 symbolic links (27467 fast symbolic links)
           1 socket
------------
      637427 files
```

I also accidentally ran it with a wrong switch (-c instead of -C0):
```
/dev/sda3: Updating bad block inode.
/dev/sda3: Inode 17302118 extent tree (at level 1) could be shorter.  IGNORED.
/dev/sda3: Inode 17317590 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 17318374 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 17319905 extent tree (at level 1) could be narrower.  IGNORED.
/dev/sda3: Inode 17320072 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 17320078 extent tree (at level 1) could be narrower.  IGNORED.
/dev/sda3: Inode 17323842 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 17325453 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 17325519 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 18612232 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 18615704 extent tree (at level 1) could be narrower.  IGNORED.
/dev/sda3: Inode 18618960 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 18619002 extent tree (at level 1) could be narrower.  IGNORED.
/dev/sda3: Inode 18630212 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 18630314 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 18633434 extent tree (at level 1) could be narrower.  IGNORED.
/dev/sda3: Inode 18633439 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 19935305 extent tree (at level 1) could be narrower.  IGNORED.
/dev/sda3: Inode 19951336 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 19951639 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 21899432 extent tree (at level 2) could be narrower.  IGNORED.
/dev/sda3: Inode 21901218 extent tree (at level 2) could be narrower.  IGNORED.

      637362 inodes used (2.04%, out of 31227904)
        7179 non-contiguous files (1.1%)
         763 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 609156/706/15
    59366901 blocks used (47.53%, out of 124894976)
           0 bad blocks
          21 large files

      539385 regular files
       68480 directories
           8 character device files
           0 block device files
           1 fifo
          75 links
       29478 symbolic links (27467 fast symbolic links)
           1 socket
------------
      637428 files
```

---

### Post by Rubi1200 on 2024-10-29
If the system is booting normally then I would say everything looks fine.

There are no critical errors or immediate warnings that would require attention.

---

### Post by peyre on 2024-10-29
Thanks!  I'll mark this solved then.

---

