---
title: "Installing 9.04 on new Desktop"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by swappo1 on 2009-06-13
Hello,

I am planning on installing 9.04 on a new desktop in which I will dual boot with vista.  I have 7.04 on my laptop but I don't remember how I did the resizing of my windows partion and the dual boot.  I remember setting up several partitions for 7.04.  How would I find out what these partitions are on my laptop so I can do the same on my desktop?  Also, how do I resize the partition for Vista?  Is it straight forward?  Thanks.

---

### Post by Therion on 2009-06-13
See this tutorial:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by raymondh on 2009-06-13
> **swappo1 said:**
>  How would I find out what these partitions are on my laptop so I can do the same on my desktop?  Also, how do I resize the partition for Vista?  Is it straight forward?  Thanks.


Hello Swappol,

On your laptop/7.04, to see how the HD looks like, you have a number of options.  Open partition editor (system > administration) or if none, download/install gparted.  It will show you the HD and  its' partition in a grahical way as well as the mount points.  Anothe roption is to open a terminal and type

sudo fdsik -l

(small L) and that will give you a text output of what is installed in your HD.

As for partitioning (you may know by now) you have the option of installing everyting within root (/) and have your swap or, creating separate partitions for root (/), home (/home) and swap.  You may do this (resizing and creating partition) prior to the actual installation.  Doing so in this manner, when you get to the acutaul install process and tha partitioning stage, you have to select MANUAL > highlight the appropriate partition > edit > USE > set file type > set the mounts (/, /home or swap) as intended.  

Another option, if you are comfortable, is to do all this partitioning during the actual install process by choosing Manual as well.  

A third option is to use GUIDED-RESIZE and use its' slider to set the space/partitions you need.  This, however, will store home, var, user, etc within root.

As it is, step 7 of the install process will allow you to review everything before proceeding.

I find 10-15 GB OK for root.  1.5 GB ok for SWAP and the rest for /home.  If you want, Bodhi wrote a good tutorial which advocates the use of /data more than /home.  See his link on the HOW-TO's

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

As for which application to use for resizing, I use gparted to resize as well as Vista's disk management utility so I know both can do the job adequately.  Remember to defrag prior to any resizing as well as back-up your files someplace else as "Murphy can come calling anytime".


Goodluck ... post back :)

Regards,

---

