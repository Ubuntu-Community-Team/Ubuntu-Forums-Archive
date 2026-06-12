---
title: "External hard disk label"
date: 2008-11-11
forum: Hardware
---

### Post by Big_Croc7 on 2008-11-11
I have an external drive formatted as XFS and I'm trying to label it so that when it mounts, it mounts with a more descriptive name than 'disk-1' etc., following this guide: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
But when I run xfs_admin -l I get:

xfs_admin: unexpected XFS SB magic number 0xeb4890d0
xfs_admin: size check failed
xfs_admin: read failed: Invalid argument
xfs_admin: data size check failed
cache_node_purge: refcount was 1, not zero (node=0x80cb210)
xfs_admin: cannot read root inode (22)
cache_node_purge: refcount was 1, not zero (node=0x80cb300)
xfs_admin: cannot read realtime bitmap inode (22)
Segmentation fault (core dumped)

I've tried reformatting it, but this happens whether I format it with GParted or using mkfs.xfs directly from the command line.  Running xfs_repair gives similar results; however, I can actually use the partition for data and it works fine.

---

### Post by platinumriver on 2009-05-31
I have the same problem. Did you ever figure this out?

---

### Post by coffeecat on 2009-05-31
There's an easy GUI way. Install gparted and xfsprogs, and you'll be able to label an xfs partition from Gparted: Partition -> Label.

---

### Post by platinumriver on 2009-06-01
Yep. Worked great. Thank you, sir.

---

