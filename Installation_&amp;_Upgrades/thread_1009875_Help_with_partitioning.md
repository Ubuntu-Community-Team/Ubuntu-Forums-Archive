---
title: "Help with partitioning"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by mahela007 on 2008-12-13
I have just replaced my hard disk, meaning it's not even formatted yet. I want to install ubuntu on the hard disk while leaving some free space (about 80GB for windows).The total capacity of the hard disk is 160 GB. Can someone tell me how to format the hard disk according to the requirements above?

---

### Post by Pumalite on 2008-12-13
Make the first partition, sda1 for Windows and format it ntfs. Install Windows first. A second partition extended; and install Ubuntu within it. At installation; go 'Manual' and choose that space.. A good scheme is:
10 GB for '/'
The rest minus 1.4 the amount of your RAM for /home
1.4 amount of your RAM for /swap

---

### Post by mahela007 on 2008-12-13
I dont have a windows CD with me at the moment, Would it be all right to install ubuntu first?

---

### Post by vanadium on 2008-12-13
It is all right, but it will be more difficult. The most easy approach is: install Windows using part of the drive, then install Ubuntu, choose "use largest free space" and Ubuntu will set up partitioning and dual boot automatically. Pumalites way is somewhat more difficult because you have to do the partitioning and indication of mount points yourself, but it is required if you prefer to have a separate /home partition.

When you install Windows after Ubuntu, you will have to set up dual boot manually yourself afterwards. Not that difficult probably (never did it myself), but an additional complexity nevertheless.

---

