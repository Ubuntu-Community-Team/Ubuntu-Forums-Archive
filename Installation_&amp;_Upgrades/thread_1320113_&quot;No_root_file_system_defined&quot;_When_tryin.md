---
title: "&quot;No root file system defined&quot; When trying to do custom partition"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by endoftheline on 2009-11-08
I’m trying to install Ubuntu 9.10 on my drive with windows 7 in a dual boot type setup.
  I booted from the Ubuntu Installer disk,( the ISO was [Ubuntu 9.10 AMD 64] 
   
  Basically I have windows 7 already installed on a partition and I want to keep it there, and I have 190GB of unpartitioned space 
   
  So in the installer I selected “Specify partitions manually”
              Then I made a new partition in the free space that was:
                          Type: Primary
  Size: 90GB
  Location for new partition: Beginning 
  Use as: Ext4 Journaling file system
  Mount Point: (I left blank)
   
  Then I hit forward and I get this error “No root file system defined”
  I’m not sure what this means, I am trying to install Ubuntu on the new 90GB partition that I just created using the Ubuntu installer. 
   
  I’m wondering if someone can point me to a more detailed install guide or one that shows how to setup the partitions to dual boot with a windows OS. I was pointed to this guide:
  [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
   
  But it was very simple, and did not show how to setup custom partitions.  
   
  Or if anyone knows what else do I need to do, please let me know.

---

### Post by AnarchyLinux on 2009-11-08
[B]Youll be fine


If you want to use the rest of your disc for Karmic just select the option (on partition manager) were it reads use largest continuous space....it will automaticly create and divide the space automatcly for you...the swap...ext...etc etc etc.[/B]

---

### Post by MountainX on 2009-11-08
> **endoftheline said:**
> 
  Mount Point: (I left blank).

The mount point must be defined. It should be root (which may be listed as a slash "/").

---

### Post by sgosnell on 2009-11-09
You have to define a mount point for root, or /.  You can't leave that box blank.  Personally, I set up two partitions, one for / and one for /home, but that's a matter of taste.  But you have to tell the OS where to put /.

---

