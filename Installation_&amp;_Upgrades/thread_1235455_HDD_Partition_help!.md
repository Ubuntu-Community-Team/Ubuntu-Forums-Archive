---
title: "HDD Partition help!"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by ruddyrum on 2009-08-09
I have a spare 80GB HDD which i split into two partitions... 60GB and 20GB! I wanted to install ubuntu on the 20GB partition, but during the install i only have the option to use the entire 80GB!?

I have now installed Ubuntu, and was wondering if i could somehow re-partition the HDD without affecteing the OS. I have a 1GB swap partition, and the rest is ext3... can i reduce the ext3 partition? If so how?

Also if i where to re-install ubuntu, what partitions would i have to setup manually? Will a 1GB swap partition and a 20GB ext3 partition suffice?

Thanks!

---

### Post by raymondh on 2009-08-09
> **ruddyrum said:**
> 

I have now installed Ubuntu, and was wondering if i could somehow re-partition the HDD without affecteing the OS. I have a 1GB swap partition, and the rest is ext3... can i reduce the ext3 partition? If so how?

Also if i where to re-install ubuntu, what partitions would i have to setup manually? Will a 1GB swap partition and a 20GB ext3 partition suffice?

Thanks!

Use the liveCD and in live session (aka TRY WITHOUT CHANGES).... access gparted thru system > adiminstration > partition editor

Gparted can shrink, delete, move, etc, partitions.  Be careful.  Post back if you need assistance or clarifications.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

If you do have to re-install, you will have to select the root (/) partition, use it as root (/) again and format to ext3.

Since you are starting your installation, have you considered separating /home form root?  That way, should you re-install for whatever reason, you can still retain config files, settings etc and just have minor cosmetic tweaks after re-installation.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Good luck.  Back-up your files first.

---

### Post by Narada on 2009-08-09
As raymondhenson said, gparted will allow you to resize your existing partitions. Basically you can shrink your ext3 partition as much as you want, as long as there is still room for the data already on it. Then you can use that free space to create another partition - perhaps /home as raymondhenson suggested - with gparted.

If you're going to do a fresh installation and want to keep it simple, I would recommend the following scheme:
[list][*]/ ext3 - 10 GB (if you like to install a ton of stuff and have plenty of room to spare bump it to 15-20 GB)
[*]/home ext3 - Everything else[/list]
By separating / and /home you've made it so that you can keep your /home data intact should you ever need to reinstall again. (You only need to reinstall to /).

---

