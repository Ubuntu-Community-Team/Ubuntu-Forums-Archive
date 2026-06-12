---
title: "Partition HD with Windows / Install"
date: 2008-10-29
forum: General Help
---

### Post by reggaematic on 2008-10-29
Hi! I have Windows 2000 installed, but I currently can't use it. I wanna be (= need to be) able to use some Windows programs today or tomorrow, so I was thinking that maybe I should install a Windows or Ubuntu & Wine on a second partition. My HD isn't partitioned at the moment though, so I was wondering if it's possible to either partition the HD using Ubuntu so that I can * install a second Windows version * or install a Ubuntu & Wine first, try the programs I want to use and if that doesn't work install a Windows version over this second partition WITHOUT risking losing my original files (GParted?). Is this even possible and is there a reasonably safe way for a n00by like me to do this, because I really don't wanna lose my old data?

---

### Post by vanadium on 2008-10-29
* If you do not want to loose your data, you must have a backup in the first place, in any circumstances
* The easiest approach to have both Windows and Ubuntu on your machine is to install Windows first, letting it use only part of the drive. Then you start the Ubuntu installation program and choose the option "Use largest free space". In this scenario, all partitioning and configuration of dual boot will be automatic.
* I understand you cannot use the currently installed Windows: you may use the live Ubuntu CD, in the live session. Using gparted, you can delete all partitions on the drive. During Windows installation, you will then instruct the Windows installer to create a partition occupying only a part of your entire drive.

---

### Post by reggaematic on 2008-10-29
Thanks for the fast reply! I guess it's also possible to install Ubuntu on the smallest partition (I would like to know that for sure before I start)? And if I let Windows partition my HD, won't I lose all data?

---

### Post by eder.apt-get on 2008-10-29
You probably will, but as mentioned before, you should do a backup first, then do anything with the partitions.

---

