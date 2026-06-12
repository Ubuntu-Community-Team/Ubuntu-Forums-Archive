---
title: "How to upgrade 8.04 to 9.04 please."
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by hardyfan on 2009-08-15
I have a notebook with 80 gig Vista and about 200 gig Ubuntu 8.04.  I've tried to install 9.04 from CD, it gives 2.5 gig to 9.04 and 196 gig (approx) to 8.04.  I would like to replace 8.04 with Jaunty and use all the space currently allocated to Ubuntu (without affecting Vista).  Can someone please point me inn the right direction ?

---

### Post by gordonh on 2009-08-15
> **hardyfan said:**
> I have a notebook with 80 gig Vista and about 200 gig Ubuntu 8.04.  I've tried to install 9.04 from CD, it gives 2.5 gig to 9.04 and 196 gig (approx) to 8.04.  I would like to replace 8.04 with Jaunty and use all the space currently allocated to Ubuntu (without affecting Vista).  Can someone please point me inn the right direction ?

Try:
sudo apt-get upgrade

If it works (it does for 9.04 to 9.10) you might have to do it twice

---

### Post by lswb on 2009-08-15
8.04 cannot be directly upgraded to 9.04. Excepting from one LTS to the next, the only supported upgrades are from one release to the next, i.e. 8.04 to 8.10 then to 9.04.

If you are not concerned about saving anything from the 8.04 installation, you can use gparted from the live CD to delete the 8.04 partition from disk, then install 9.04 in the space that was freed. Another option is to use gparted (after backing up whatever you want to save, of course) to shrink the 8.04 partition and then install 9.04 into the freed space, with triple booting.

---

### Post by raymondh on 2009-08-15
> **lswb said:**
> 8.04 cannot be directly upgraded to 9.04. Excepting from one LTS to the next, the only supported upgrades are from one release to the next, i.e. 8.04 to 8.10 then to 9.04.

If you are not concerned about saving anything from the 8.04 installation, you can use gparted from the live CD to delete the 8.04 partition from disk, then install 9.04 in the space that was freed. Another option is to use gparted (after backing up whatever you want to save, of course) to shrink the 8.04 partition and then install 9.04 into the freed space, with triple booting.

Or, you can install over the existing 8.04 partition.  Set mountpoint to '/' .... check the format box, as well as choosing which (ext3 or ext4).  For swap, you can do the same over the existing swap, setting as 'swap file system'.  If you currently have a separate /home, set mountpoint to '/home' but **DO NOT FORMAT**.

Note the above will reformat, hence erase all current settings, files, etc.  Back-up your files first.

If you wish to establish a separate /home now, I suggest using gparted from the liveCD to delete the old ubuntu and create the necessary partitions and it's file formats (root, /home, swap).  See the guide by [D. Falco (starting post#8 )]("http://ubuntuforums.org/showthread.php?t=1175277") if you want to go this route.

If you decide not to mess with gparted/partitioning/manual installations and choose instead to do a network upgrade, make sure you are updated in each version before upgrading to the next (update 8.04 > upgrade to 8.10 > update 8.10 > upgrade to 9.04 > update 9.04)

[Upgrade notes from 8.04 to 8.10 to 9.04.]("https://help.ubuntu.com/community/UpgradeNotes")

Good luck.  Back up your files. Post back if you need clarifications.

---

