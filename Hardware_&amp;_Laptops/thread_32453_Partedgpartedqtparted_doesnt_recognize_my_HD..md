---
title: "Parted/gparted/qtparted doesnt recognize my HD."
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by void_false on 2005-05-07
Hello all! 
I want to preform a simple task - resize my ubuntu partition. I've searced the forum and found that I need to use *parted with all hd unmounted. So I booted Knoppix and ran parted. Here started my story. *parted doesnt recognize my HD well. It says I have one partition:
```

Minor    Start       End              Filesystem  Flags
1           0.000      29325.515   fat16

```
What the hell? I have 9 partitions and free space after 9th one. Here's fdisk print.
```
   
Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         511     4104576    b  W95 FAT32
/dev/hda2             512        3738    25920877+   f  W95 Ext'd (LBA)
/dev/hda5             512        1595     8707198+   b  W95 FAT32
/dev/hda6            1596        3157    12546733+   b  W95 FAT32
/dev/hda7   *        3158        3162       40131   83  Linux
/dev/hda8            3163        3225      506016   82  Linux swap
/dev/hda9            3226        3633     3277228+  83  Linux

```
gparted/qtparted say same thing as parted (just in graphical form)
I've read somewhere that parted have problems with large HDs (is 30gb large?!). So i installed dfsee. It shows my partitions right, but doesnt allow me to expand my ext3 partition!
Please help.

---

### Post by void_false on 2005-05-08
Well. I´ve used another tool to resize my partition. First I converted it to ext2, then resized it with Partition Magic, then added journalazing (converted to ext3).

But my question is. Why the heck parted doesnt recognize my partition table???!!!

---

