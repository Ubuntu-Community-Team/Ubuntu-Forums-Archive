---
title: "Pre-Installation question"
date: 2005-01-16
forum: Installation &amp; Upgrades
---

### Post by rbrugman on 2005-01-16
Hello,
I am going to install Ubuntu, but I'm wondering what the best way to go about it would be.  I would like to use seperate partitions so I can easily upgrade to a new version of the OS without losing all of my user data.  Does anyone have a recommendation?

Thanks,
Robert

---

### Post by Rancoras on 2005-01-16
Yes, a separate partition is possible.  If you have unpartitioned space on your HDD, use that.  There is a partitioner available during the install process.  Make sure you have a good backup of any data you don't want to lose.  Good luck.  :D

---

### Post by Xian on 2005-01-16
[QUOTE=rbrugman] I would like to use seperate partitions so I can easily upgrade to a new version of the OS without losing all of my user data.  Does anyone have a recommendation?[/QUOTE]
Just include a separate /home partition during the Ubuntu installation. Something like:

/dev/hda1 ntfs        winxp
/dev/hda2 swap
/dev/hda3 reiserfs   /
/dev/hda4 reiserfs   /home

---

### Post by drbista on 2005-01-21
Dear Xian:

I have the same question, but at what stage should I mount the different partitions?

I have posted my problem at [http://ubuntuforums.org/showthread.php?p=52804#post52804](http://ubuntuforums.org/showthread.php?p=52804#post52804)

Help solicited. Thanks!

---

