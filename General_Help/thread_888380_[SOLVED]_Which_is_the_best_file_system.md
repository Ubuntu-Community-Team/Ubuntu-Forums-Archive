---
title: "[SOLVED] Which is the best file system"
date: 2008-08-13
forum: General Help
---

### Post by Chikitulfo on 2008-08-13
I bought a new computer and I installed XP (gaming) and Ubuntu.
So I have a partition for xp and another one for ubuntu, and I've been thinking to use a third partition to store files that both ubuntu an windows can read and write without any problem.

The question is, which is the best file system for this partition in order to have both of the OS's writing on it?

The catch is: I need to store some single files that weight from 5 to 8GB and maybe more, so fat32 doesn't work.
And I don't know if ntfs is the best choice for ubuntu.


Thanks in advance!

---

### Post by justleen on 2008-08-13
fat32 is nativly supported by both.
Personlly, I just use ext2/3 and installed [this ]("http://www.fs-driver.org/")driver in XP to access the ext3 partitions

---

### Post by Chikitulfo on 2008-08-13
Yeah but fat32 doesn't allow file sizes of more than 4GB, and I i have a few files that weight something between 5 and 8GB.

Windows can write without issues in ext3 with that driver?

---

### Post by justleen on 2008-08-13
i've been using it for quite some time, the ext3 driver, and i havent had any problems yet. And I've copied quite a bit of data back and forth (game iso's...)
I even installed windows-stuff on a ext3 parition and thats works just fine..

---

### Post by Rainstride on 2008-08-13
i use ntfs, i haven't had any problems that i can see so far.

---

### Post by Chikitulfo on 2008-08-13
I'll try both of them out, and i'll choose the one i like the most


Thanks a lot!!

---

### Post by Crafty Kisses on 2008-08-13
> **justleen said:**
> i've been using it for quite some time, the ext3 driver, and i havent had any problems yet. And I've copied quite a bit of data back and forth (game iso's...)
I even installed windows-stuff on a ext3 parition and thats works just fine..

Yeah, same here, ext3 works perfectly for me.

---

