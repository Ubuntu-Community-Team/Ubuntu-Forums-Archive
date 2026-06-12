---
title: "can't mount 2nd hdd, reiserfs"
date: 2005-11-07
forum: Hardware &amp; Laptops
---

### Post by visctrix on 2005-11-07
Trying to get access to files saved when using Xandros on hdf1, a new disk not yet used for anything else.  I've spent a couple of hours looking at the Ubuntu Wiki and posts on this forum, and I have managed to mount hde6 ok, but hdf1 is not working.

Following advice I did this:

[INDENT]visctrix@x1-6-00-30-bd-b1-72-6fUbuntu:~$ for i in `ls /dev/hd* | grep -e "hd\w$"`; do sudo fdisk -l $i; done
Password:

Disk /dev/hde: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        2432    19535008+   c  W95 FAT32 (LBA)
/dev/hde2            3375        4998    13044780    5  Extended
/dev/hde3            2433        3374     7566615   83  Linux
/dev/hde5            3375        3439      522081   82  Linux swap / Solaris
/dev/hde6            3440        4998    12522636   83  Linux

Partition table entries are not in disk order

Disk /dev/hdf: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1       10011    80413326   83  Linux

[/INDENT]Then I created a directory: 
[INDENT]sudo mkdir /media/hdf1[/INDENT]

Then editing /etc/fstab I added the line:
[INDENT]/dev/hdf1       /media/hdf1     reiserfs    defaults    0       0[/INDENT]

But when I do: sudo mount -a  I get an error message:
[INDENT]mount: Operation not supported[/INDENT]

The same process worked perfectly when I used the same syntax for hde6.

Any suggestions?

Thanks

---

### Post by mlomker on 2005-11-07
That's odd.  Have you tried it just from the command line?

```

sudo mount -t reiserfs /dev/hdf1 /media/hdf1

```

---

### Post by visctrix on 2005-11-07
same message: 

mount: Operation not supported

---

### Post by mlomker on 2005-11-07
What are you getting in **dmesg** after the attempt?

You could also try mounting it read-only to see if it is a possible corruption issue:

```

sudo mount -t reiserfs -o ro /dev/hdf1 /media/hdf1

```

---

### Post by visctrix on 2005-11-07
dmesg gives:
     [4308279.177000] ReiserFS: hdf1: found reiserfs format "3.6" with standard journal
     [4308283.574000] ReiserFS: hdf1: using ordered data mode
     [4308283.594000] ReiserFS: hdf1: journal params: device hdf1, size 8192, journal first block 18, max trans len 1024, max batch 900, max   commit age 30, max trans age 30
     [4308283.598000] ReiserFS: hdf1: checking transaction log (hdf1)
     [4308283.655000] ReiserFS: warning: is_tree_node: node level 1 does not match to the expected one 2
     [4308283.655000] ReiserFS: hdf1: warning: vs-5150: search_by_key: invalid format found in block 32770. Fsck?
     [4308283.655000] ReiserFS: hdf1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [1 2 0x0 SD]
     [4308283.655000] ReiserFS: hdf1: Using r5 hash to sort names
     [4308283.655000] ReiserFS: hdf1: warning: xattrs/ACLs enabled and couldn't find/create .reiserfs_priv. Failing mount.


if i try to mount read-only I get 
        mount: /dev/hdf1: can't read superblock

thanks

---

### Post by mlomker on 2005-11-07
[QUOTE=visctrix]sorry, how do i find that out?
[/QUOTE]

Type **dmesg** in a terminal.  That's just a command-line utility that reads and formats the /var/log/kern.log file.

---

### Post by visctrix on 2005-11-07
So that looks like the disk is corrupted.  Can I save any of the data?  Where should I look for guidance?

Thanks

---

### Post by mlomker on 2005-11-07
Try repairing it:

```

sudo reiserfsck --fix-fixable /dev/hdf1

```

---

### Post by visctrix on 2005-11-07
I got this:

reiserfsck --fix-fixable started at Tue Nov  8 01:08:48 2005
###########
Replaying journal..
Reiserfs journal '/dev/hdf1' in blocks [18..8211]: 0 transactions replayed
Checking internal tree../  1 (of  11)block 32770: The level of the node (1) is not correct, (2) expected
 the problem in the internal node occured (32770), whole subtree is skipped
finished
Comparing bitmaps..vpf-10630: The on-disk and the correct bitmaps differs. Will be fixed later.
Bad nodes were found, Semantic pass skipped
1 found corruptions can be fixed only when running with --rebuild-tree
###########
reiserfsck finished at Tue Nov  8 01:08:59 2005

---

### Post by mlomker on 2005-11-07
> can be fixed only when running with --rebuild-tree


I guess you'll want to do that, then.

---

### Post by visctrix on 2005-11-07
Thank you - I can access most of my old files now (I got a message saying 12 were corrupted and deleted)

:-)

---

