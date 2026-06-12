---
title: "upgrade problem 7.10 to 8.04"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by stoppage on 2009-03-07
On an upgrade from 7.10 to 8.04 Ubuntu refused the restart....on a maintenance shell it registered „fsck died with exit status 8...file system check failed, please repair manually“. Apparently its a problem with hda7, home folder. Can somebody please help me out here?

---

### Post by taurus on 2009-03-07
Did it drop you into a prompt?  If it did, run

```
fsck /dev/hda7
```
if that is the one that it complains.

Otherwise, you need to boot with Ubuntu LiveCD and run fsck from there.

Applications -> Accessories -> Terminal
```
sudo fsck **/dev/hda7**
```
Make sure it is really /dev/hda7 because it could be **/dev/sda7**!

```
sudo fdisk -l
```

---

### Post by stoppage on 2009-03-07
fsck shows partition is ok....

Reiserfs journal '/dev/hda7' in blocks [18..8211]: 0 transactions replayed 
Checking internal tree..finished 
Comparing bitmaps..finished 
Checking Semantic tree: 
finished 
No corruptions found 
There are on the filesystem: 
        Leaves 1381 
        Internal nodes 10 
        Directories 1310 
        Other files 7356 
        Data block pointers 141685 (2568 of them are zero) 
        Safe links 0 
########### 
reiserfsck finished at Sun Mar  8 04:57:40 2009

---

### Post by stoppage on 2009-03-15
The solution....this upgrade changes partition designations. fdisk -l "sees" sda and sdb, so hda... doesn't exist. Proper info needs to be then inserted in fstab. Solved...thank you

---

