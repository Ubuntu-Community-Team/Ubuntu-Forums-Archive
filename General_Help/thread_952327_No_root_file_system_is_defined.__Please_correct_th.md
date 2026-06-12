---
title: "No root file system is defined.  Please correct this from the partitioning menu"
date: 2008-10-19
forum: General Help
---

### Post by Taz. on 2008-10-19
Hi all. i have a problem.

When i install ubuntu, i press Manual and i get this :

/dev/sda1 NTFS
/dev/sda2 NTFS
/dev/sda3 NTFS

The ones above, is the computers hardrive. which i dont want.

/dev/sdb1 NTFS
/dev/sdb5 swap
/dev/sdb3 NTFS

here is 1 external hard drive with 2 partitions. The /dev/sdb1 is the main HDD of all, and then i have no clue whats swap, but i know that, i did the /dev/sdb3 partition. Its there i wanna install my ubuntu.

So i press it and i press forward, i get this : No root file system is defined.  Please correct this from the partitioning menu.

What to do? Remmeber im new to this, i heard bout commmand lines, i got no idea what they are. So be specific, thanks in advance.

---

### Post by bodhi.zazen on 2008-10-19
As a part if installing you need to specify a partition for root or /

NTFS can not be used as the file system for root. So select the appropriate partition.

---

### Post by Taz. on 2008-10-19
> **bodhi.zazen said:**
> As a part if installing you need to specify a partition for root or /

NTFS can not be used as the file system for root. So select the appropriate partition.


What do u mean by the / ? I want a type of HDD were both windows and linux can read it..

---

### Post by bodhi.zazen on 2008-10-19
/ = the "root partition" 

/ is where Ubuntu is installed, it is the Linux equivalent of C:\

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

    [uhelp]community/Installation[/uhelp]

---

