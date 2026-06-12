---
title: "shared ext3 partition fs-driver"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by ZootHornRollo on 2009-03-06
Hi,

i have re-installed my XP/Kubuntu dual boot.  I am using a shared ext3 partition for /home.

I am trying to use fs-driver to allow windows to read/write the partition.

after running fs-driver i got an error saying my ext3 partitions weren't formated.

So iran the fsdriver mount diag and it tells me my partition is formatted incorrectly - something to do with being 256, not 128.

i read up a little on this before reformatting my HD and purposely used gparted from an 8.04 disk to do the partitioning then installed kubuntu 8.10.

any way i can retrospectively reformat my /home partition in 128?

---

### Post by Skripka on 2009-03-06
What is the exact error that widnows spits back at you?

The Ext windows driver, last I knew supported Ext2 fully...with ext3 just happening to work, whilst not being officially supported.

---

### Post by ZootHornRollo on 2009-03-06
it says something like "inode size is more than 128 (inode size is 256)"

---

### Post by ZootHornRollo on 2009-03-06
```
The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not
mount it because the file system has an inode size unequal to 128 bytes (inode
size: 256 bytes).
The only way to solve it is to back up the volume's files and format the file
system: give the mkfs.ext3 utility the -I 128 switch. Finally, restore all
backed-up files.
After that, the Ext2 IFS software should be able to access the volume.
```

---

### Post by ZootHornRollo on 2009-03-06
i don't mind starting from scratch on the /home as i have only just set everything up and don't actually have anything on it yet.

---

### Post by ZootHornRollo on 2009-03-06
would reinstalling ubuntu be the best course of action?

would that allow me to set the inodes?

---

### Post by maybeway36 on 2009-03-06
You could use a different ext2/3 Windows driver. I think there are at least two.

---

### Post by ZootHornRollo on 2009-03-06
i know of two other programs that allow read access to ext3 but only fs-driver allows read & write.

is there another that allows read & write?

p.s.  i tried running mkfs from a live disk

> sudo mkfs.ext3 /dev/sda2 -I 128

it did something to the partition but its now fooked!  8)  windows could access it, i replace the /home files but kubuntu would not boot at all.

i'm goign to have to reformat it again!

will maybe just make do with read access from windows!

---

### Post by lordgafal on 2009-04-03
ext2fsd works perfectly with modern linux inodes size and keeps being updated 

read & write

ext2fsd.sourceforge.net/

---

