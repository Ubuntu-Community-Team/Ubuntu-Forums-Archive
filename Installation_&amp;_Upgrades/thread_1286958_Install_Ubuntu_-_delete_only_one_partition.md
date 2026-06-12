---
title: "Install Ubuntu - delete only one partition"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by AlexandruH on 2009-10-09
I tried to find in the archives a solution but I was unable to.

First time user of Ubuntu. I'm trying to install it in a computer with three partitions: C, D and E. I only want to get rid of C (and replace XP with Ubuntu), but keep the data from D and E. Now, I'm at the manual install section and I'm a bit lost, since I'm not sure what option would allow me to keep the data from those two partitions... I can't move it somewhere else, since my windows version is a total failure at this point...

---

### Post by ajgreeny on 2009-10-09
Just to be certain, lets see the output from the terminal in live CD of ```
sudo fdisk -l
```Copy everything that appears back here, including all the asterisks etc etc.  That will give us more certainty about which is the boot partition, ie your windows OS, rather than the data partitions.

Once you know that you can use System ->Administration ->Partition Editor to delete the windows OS partition and make unallocated space into which you can then install ubuntu by making new partition table in that space and partitioning however you want it.

Have a look here for more info.
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by AlexandruH on 2009-10-09
Problem solved. I took a risk... and suceeded... :)

Ubuntu looks... great. Simply f****** great...

---

### Post by ajgreeny on 2009-10-10
And it gets better and better the more you look and use!

---

