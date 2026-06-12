---
title: "&quot;No Root File System Detected&quot;"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by Gunmetal_Ghoul on 2008-12-03
I downloaded the alternative install ISO and burned a copy to install. After choosing 30GB for the partitioning I came across the message "NO ROOT FILE SYSTEM DEFINED"  before I could finalize the partition. It may mean that I have to retrace my steps somewhere, but what does it really mean and what do I do?

---

### Post by jenkinbr on 2008-12-03
Did you use manual partitioning?  If so, you need to specify a mount point for each drive you want to use.  At the very least, you must include a drive that will be mounted to '/'.  Not doing this will generate this error.

[IMG]http://3.bp.blogspot.com/_SxnEyE2bzLI/SCcKJb9UzbI/AAAAAAAAC2c/tXp83VPmt_k/s1600/19dscn2271.jpg[/IMG]
In the above image, <which apparently broke overnight> note that the mount point is set to 'none'.  You will want this set at '/' for your root partition, as in the images below.
[IMG]http://bp3.blogger.com/_SxnEyE2bzLI/SCcKrr9UzdI/AAAAAAAAC2s/cqySTk7Kbx0/s400/21dscn2275.jpg[/IMG]
and 
[IMG]http://bp0.blogger.com/_SxnEyE2bzLI/SCcKr79UzeI/AAAAAAAAC20/nD8Q-U3Yak0/s400/22dscn2276.jpg[/IMG]

Images from:
[http://afifplc.blogspot.com/2008/05/ubuntu-studio-edition-804-installation.html](http://afifplc.blogspot.com/2008/05/ubuntu-studio-edition-804-installation.html)

Of course, this assumes you are using manual partitioning.

---

### Post by Gunmetal_Ghoul on 2008-12-03
I ended up trying the partitioning for the hard drive at 105 GB for Windows and 55 GB for Ubuntu. It didn't end up like that at all. I made two partitions but there are also two sets of free space leftover. I tried to resize them but I don't know how to assimilate the free space into a partition.

---

### Post by Gunmetal_Ghoul on 2008-12-04
I finally got it installed, but there are now some video/graphics problems when I boot it. Another challenge to meet....

---

