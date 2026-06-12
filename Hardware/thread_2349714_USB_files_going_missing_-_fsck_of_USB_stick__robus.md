---
title: "USB files going missing - fsck of USB stick / robust file copy (recursive)"
date: 2017-01-17
forum: Hardware
---

### Post by steve234 on 2017-01-17
Hi there,

I'm transferring some holiday vids onto my mate's 128gb usb stick. 

I've just been dragging and dropping from PC-man-FM - it all appears to be going well but once the stick is unmounted and re-mounted, or used in a different machine, the folders remain but some or all of the files disappear.

So far I've done the following:

Create a new 128gb fat32 partion with Gparted

Found the usb stick (fdisk -l)

```
Disk /dev/sdb: 134.2 GB, 134217728000 bytes
255 heads, 63 sectors/track, 16317 cylinders, total 262144000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb729f37b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   262143999   131070976    b  W95 FAT32


```

un-mounted it in PC-man-FM and used fsck on it - with no results.

```
$ sudo fsck /dev/sdb1
fsck from util-linux 2.20.1
fsck.fat 3.0.26 (2014-03-07)
/dev/sdb1: 1 files, 1/4094967 clusters

```

What gives? 

Is the stick faulty?

 Is PC-man-FM simply not the right tool to use? 

Should I be using something more robust like "cp -r" in the terminal? 

Do I need to mount / unmount in the terminal also (PC-man-FM handles mounting and "ejecting").

If someone has any ideas I'd appreciate them.

---

### Post by TheFu on 2017-01-19
fat32 has file size limitations.  I thought fat32 wasn't supported by MSFT for more than 32G flash drives.

Did you "flush" the disk buffers?  Type (don't copy/paste) **sync; sync ;sync ; ** this is an old-school admin thing.

---

