---
title: "Remove XP and realocate space to Ubuntu"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by rslater on 2009-06-25
OK, so I have finally had it with XP.  I have a dual boot system with XP on one hard disk, which is partitioned with Windows on the 1st partition and a data area on the 2nd partition.  I have a 2nd hard disk which has Ubuntu on it and a small amount of data.

I now want to completely remove windows.  Reuse the space for Ubuntu and remove the dual boot menu so that Ubuntu loads as default.

As I am completely new to this, any help would be appreciated.  Thanks in advance.

---

### Post by raymondh on 2009-06-25
> **rslater said:**
> OK, so I have finally had it with XP.  I have a dual boot system with XP on one hard disk, which is partitioned with Windows on the 1st partition and a data area on the 2nd partition.  I have a 2nd hard disk which has Ubuntu on it and a small amount of data.

I now want to completely remove windows.  Reuse the space for Ubuntu and remove the dual boot menu so that Ubuntu loads as default.

As I am completely new to this, any help would be appreciated.  Thanks in advance.

How do you want to "reuse the space for ubuntu" in the first drive?  Are you wanting to keep the space as a data/media area while ubuntu resides in the 2nd hard disk?

Some reading materials to familiarize yourself with what you may be about to do:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Also, back up pls.

---

### Post by RedSingularity on 2009-06-25
Use the Partition editor in Ubuntu to reformat the HDD.  You need to boot ubuntu from a live CD and then use the editor from there.  Just type in terminal "sudo gparted"

---

