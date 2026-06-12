---
title: "possible to install over hardy and keep home folder?"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by uschxc on 2009-05-14
I did the upgrade to jaunty a couple days ago and agreed to all of the configuration file changes but I'm not sure everything went as it should.  I booted to a livecd to covert my file system to ext4 and noticed several services that were running that weren't even set up on my system such as 

mount-all-bootclean
mountall
mountdevsubfs
mountkernfs
mountnfs-bootclean
mountnfs
mountoverflowtmp

i did a comparison of running services to determine which ones i could turn off as my system start up time was painfully slow.  its a little snappier now after disabling mysql and some other unneeded services, but i would love nothing more than to to a fresh install but keep my home directory and re-add applications as needed.... is this possible?

---

### Post by Mark Phelps on 2009-05-16
You could read the link below, move your /home to its own partition, and reinstall using manual partitioning with NOT reformatting the /home partition:

[http://ubuntuforums.org/showthread.php?t=46866&highlight=moving+home+partition]("http://ubuntuforums.org/showthread.php?t=46866&highlight=moving+home+partition")

---

### Post by uschxc on 2009-05-16
this would work but my disk is currently a monolithic partition.

---

### Post by pauna on 2009-05-16
> **uschxc said:**
> this would work but my disk is currently a monolithic partition.

You can use gparted to shrink your current monolithic partition and create a new partition to the newly freed space. To do this you need to boot to a live Ubuntu cd (which you should have?) which includes gparted.

Alternatively, if your home folder is less than 2GB, you could upload it to an online sync service like Dropbox, which has a native Linux client. The free basic account gives you 2GB free space. I used this method when I did a complete reinstall of my laptop. 

If you are interested in Dropbox, use my referral link [https://www.getdropbox.com/referrals/NTE2NzY5Mzk](https://www.getdropbox.com/referrals/NTE2NzY5Mzk) and we both get some extra free disk space.

---

