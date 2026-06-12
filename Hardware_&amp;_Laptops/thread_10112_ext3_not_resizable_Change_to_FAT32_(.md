---
title: "ext3 not resizable? Change to FAT32? :("
date: 2005-01-04
forum: Hardware &amp; Laptops
---

### Post by Quest-Master on 2005-01-04
Is it not possible to resize an ext3 partition? I've tried QtParted on both the SysReccd and Knoppix LiveCD.. not to mention the command-line parted. QtParted doesn't allow the resize option to be selected, and parted says it can't resize it. Both the programs can resize my fat32 partition though. :(!!!

This troubles me as I need to resize partitions often. Plus, this troubles me even more because if I have to reinstall to make sure I set the filesystem as fat32, this would be my fifth Ubuntu install in a month. :\

Any help would really be appreciated.

---

### Post by Quest-Master on 2005-01-05
I can't make a partition through QtParted or Parted either.

partition magic come back to me :(

---

### Post by az on 2005-01-05
ext3 is most deffinitely resizeable.

You may not modify a mounted partition.

In QT parted, you make all your changes and then select commit.  Is this the problem?  If not, what version of parted (not qtparted) are you using?

Also, from the parted website, in relation to resizing:
# For ext2, ext3 and reiserfs: the start of the partition must stay fixed.

---

### Post by Quest-Master on 2005-01-05
[QUOTE=azz]Also, from the parted website, in relation to resizing:
# For ext2, ext3 and reiserfs: the start of the partition must stay fixed.[/QUOTE]

I won't be able to resize it then. :(

---

### Post by az on 2005-01-06
Well, that depends.  With qtparted, you can do several steps and tell it to go.  For example, you can shrink another partition enough to _move_ your ext3 partition there, then move it back to the spot where you need it to go.  The limitation of not shrinking a partition without changing the starting point is so that it does not write over itself.

No partitionner will be able to do this unless you have enough free space to move things around like that.

---

### Post by Quest-Master on 2005-01-06
Is there a move option in QtParted?

---

### Post by az on 2005-01-06
Probably.  It may be copy.  Parted does.

2.4.8 move


Command: move minor start [end] 
Moves partition on the disk, by moving its beginning to start. Note: move never changes the minor number. 

If no end is given, the partition's size remains the same. 

Supported file systems: 

ext2, ext3 (provided the destination partition is larger than the source partition) 
fat32 
fat16 
linux-swap 
reiserfs (if libreiserfs is installed) 
Example: 

(parted) move 2 150

Move partition with minor number 2 so that it begins 150 megabytes from the start of the disk. 





Anyway.  You can just use your ubuntu boot cd.  It's partitioner can move(copy) data from one partition to another.  It is easy.

---

