---
title: "Cannot mount HDD"
date: 2015-02-06
forum: Hardware
---

### Post by Peptid on 2015-02-06
Dear All,

Variant of this problem may be common but I couldn't solve it.

I have a 1 TB Silicon Power External hdd. It is formatted with gparted, using ext4 and gpt.

Everything was working fine till today. I unmounted it with 

sudo umount /media/directory

Since then, I cannot mount it by any means.

Here I post the outputs of commands I tried.

```
sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004d6da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    97867775    48932864   83  Linux
/dev/sda2        97869822   976771071   439450625    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5        97869824   898648063   400389120   83  Linux
/dev/sda6       898650112   976771071    39060480   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000bf9e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001   83  Linux
Partition 1 does not start on physical sector boundary.
```

```
sudo mount -t ext4 /dev/sdb /media/peptid/
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

[HTML]/usr/bin/udisks --mount /dev/sdb
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error[/HTML]

I opened gparted, and it says 'filesystem is unknown'

```
/usr/bin/udisks --mount /dev/sdb --mount-fstype ext4
Mount failed: Not a mountable file system


```

I have very important data in it, so I have to save.

Any help would be greatly appreciated.

---

### Post by weatherman2 on 2015-02-06
"/dev/sdb" is the device ID of the disk, not the partition you are trying to mount.

"/dev/sdb1" is the partition's device ID.  So you want this:

```
sudo mount /dev/sdb1 /media/peptid/
```

with "sdb" replaced by "sdb1" (and you shouldn't need the -t ext4).

If you have important files on that drive, you're taking a big chance not having them backed up.  Hard drives fail all the time, sometimes without warning, and you are taking a risk that you might lose your data if/when the drive fails.  And any external hard drive could easily fall from a table while operating or something, and that could be fatal for the drive.  Best advice is to have a second identical drive, if possible, that is an exact copy of the other one and sync them from time to time.  Or make sure the 1TB is backed up elsewhere, regularly.

---

### Post by yancek on 2015-02-06
The command:  sudo parted -l will show the filesystem type of mounted or unmounted partitions.  What you did wrong in your mount command is to try to mount the entire drive rather than the filesystem on the partition, add a 1 to sdb, from your fdisk:

> sudo mount -t ext4 /dev/sdb1 /media/peptid/

---

### Post by Peptid on 2015-02-07
Hello,

I followed both comments, yet -t ext4 option seems to be a must; mount command complained that fs type must be specified.

```
sudo mount -t ext4 /dev/sdb1 /media/peptid
``` also did not work. 

Now I am able to solve the problem. I tried 
```
fsck.ext4 /dev/sdb1
``` 
then it somehow solved all the problems above. After fsck completes, I am able to mount without any problem. 

Thank you for your replies.

---

### Post by yancek on 2015-02-07
Corrupt filesystems will prevent mounting and that was the correct action, as you found.

---

