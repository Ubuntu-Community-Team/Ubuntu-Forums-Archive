---
title: "Lost partition"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by zorglub76 on 2009-01-11
Hi all,

I've installed Ubuntu 8.10 on external hd (wd passport) by creating two new partitions there (swap and /). I've created these partitions by resizing the existing one (which had ~120GB of data) from 160GB to 140GB, and then using unallocated space to create partitions.

Now i can't see the partition with data (the original partition)

Actually, I can't mount it. fdisk -l gives me this for sdb:

/dev/sdb1               2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sdb5               2       17630   141604911    7  HPFS/NTFS
/dev/sdb6           17631       17814     1477948+  82  Linux swap / Solaris
/dev/sdb7           17815       19457    13197366   83  Linux

I need sdb5.

Any idea what I could do?

Windows XP storage manager sees it as a healthy NTFS partition, and EASEUS Partition Manager sees it as unformatted partition. Seems that all data is still there, but I can't reach it...

Thanks in advance!

---

### Post by logos34 on 2009-01-11
try this:

sudo mkdir /media/windows

sudo mount -t ntfs-3g -o force /dev/sdb5 /media/windows 

anything?

OR to automount:

edit fstab:

gksudo gedit /etc/fstab

add this line:

> /dev/sdb5 /media/windows ntfs-3g defaults 0 0 

or run ntfs-config to auto edit fstab:

sudo apt-get install ntfs-config

sudo ntfs-config

->'enable write support' external device

---

### Post by zorglub76 on 2009-01-11
I tried ntfs-config, but it didn't help (found only some sda partition).
Then i tried the first solution you provided, but got the following:
[I]
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sdb5': Invalid argument
The device '/dev/sdb5' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?[/I]

---

### Post by logos34 on 2009-01-11
do you have a windows installation you can run error checking (chkdsk /r) on sdb5? Either that or maybe 'unclean shutdown' issue is preventing linux from mounting it. (if the latter, you need to go through the proper procedure for disconnecting/shutting down a usb drive)  hard to tell.  

or maybe try simply

sudo mount -t ntfs /dev/sdb5 /media/windows

---

