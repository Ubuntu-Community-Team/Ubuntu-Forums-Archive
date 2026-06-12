---
title: "External 500GB HardDrive will not mount"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by utjacob on 2007-02-12
Ubuntu 6.10 Edgy (New User)
I have an external 500GB Hard drive that i need to be able to read when i try to mount it in the file browser it gives me this error  when i attempt to mount it....

Unable to mount the selected volume.
Details.
mount: operation not supported

error: could not execute pmount

When i type dmesg in the terminal i get this
[17195734.920000] ReiserFS: sdd1: found reiserfs format "3.6" with standard journal
[17195767.076000] ReiserFS: sdd1: using ordered data mode
[17195767.100000] ReiserFS: sdd1: warning: sh-461: journal_init: wrong transaction max size (3348812201). Changed to 1024
[17195767.100000] ReiserFS: sdd1: journal params: device sdd1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 2014914534, max trans age 30
[17195767.100000] ReiserFS: sdd1: checking transaction log (sdd1)
[17195768.320000] ReiserFS: warning: is_tree_node: node level 517 does not match to the expected one 1
[17195768.324000] ReiserFS: sdd1: warning: vs-5150: search_by_key: invalid format found in block 8211. Fsck?
[17195768.324000] ReiserFS: sdd1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [1 2 0x0 SD]
[17195768.324000] ReiserFS: sdd1: Using r5 hash to sort names
[17195768.324000] ReiserFS: sdd1: warning: xattrs/ACLs enabled and couldn't find/create .reiserfs_priv. Failing mount.
[17196082.672000] ReiserFS: sdd1: warning: unknown mount option "umask=000"
[17196231.296000] fuse init (API version 7.6)

utjacob@utjacob-desktop:/$ sudo fdisk -l
...
Disk /dev/sdd: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    7  HPFS/NTFS

---

