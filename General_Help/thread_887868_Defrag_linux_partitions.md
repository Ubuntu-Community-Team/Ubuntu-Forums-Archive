---
title: "Defrag linux partitions"
date: 2008-08-12
forum: General Help
---

### Post by e24ohm on 2008-08-12
Do i need to defrag linux partitions? If so, how do i do this?

Thank you,
E

---

### Post by Titan8990 on 2008-08-12
No, ext3 doesn't need to be defragged (even though to may fragment over time). When ext4 is released it will have a defrag feature.

[http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

---

### Post by OutOfReach on 2008-08-12
There is no need to defrag Linux filesystems. :)
The only time they get a little fragmented is when the disk is really full, so there is really no need to worry!

Cheers

---

### Post by Dr Small on 2008-08-12
You don't need to defragment ext3.

---

### Post by perlluver on 2008-08-12
No you do not need to defrag a Linux partition, they are made to do this automatically, in future releases there may be a Defrag option.

---

### Post by e24ohm on 2008-08-12
thanks.

---

### Post by WRDN on 2008-08-12
For an ext3 filesystem to become fragmented, you must usually have 90%+ disk usage.
This is because, in short, when you create a file on the ext3 filesystem, the files are spread out, and have ample room to grow. This is in contrast to the likes of the NTFS filesystem where files are placed next to each other, and if you ever edit a file, the file may grow- the data will then need to be placed on another part of the disk. With ext3 this does not happen, so you don't need to defragment the filesystem.

---

### Post by peakshysteria on 2008-08-12
What about other HDD's? For some odd reason I seem to have one NTFS HDD and one FAT32 in addition to the HDD with Ubuntu on it. Do I need to fragment those? I run Ubuntu single boot.

---

### Post by eldragon on 2008-08-12
> **peakshysteria said:**
> What about other HDD's? For some odd reason I seem to have one NTFS HDD and one FAT32 in addition to the HDD with Ubuntu on it. Do I need to fragment those? I run Ubuntu single boot.

to fragment is a bad thing, so you shouldnt do that :D

besides that smartass comment....you need to defrag those, i havent seen a fat32 / ntfs defrag tool around...there might be one though.... :(

---

### Post by peakshysteria on 2008-08-12
Ops..a bit fast there :) Not to keen on defragmenting anyway. Didn't do it to often when I ran Windows either.....just curious..

---

