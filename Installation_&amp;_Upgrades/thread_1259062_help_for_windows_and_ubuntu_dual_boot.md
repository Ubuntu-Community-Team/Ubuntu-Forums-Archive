---
title: "help for windows and ubuntu dual boot"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by trojanworrier on 2009-09-05
I've partitioned my hard drive as follow using gparted:

/dev/sda1  - ntfs  <--windows 7
/dev/sda2  - ext3  <-- want to install linux, but :( i can't
/dev/sda3  - linux-swap 
/dev/sda4  - ntfs  <--data

i installed windows 7 first. now im trying to install linux. but it gives me an error msg "no root file system is defined" while trying to install it in ext3.

please advice.

---

### Post by Partyboi2 on 2009-09-05
Hi, when you get to the partitioning part of the install, choose "Manual" and edit your /dev/sda2 partition so that the mount point is set to / and that the partition is set as a ext3.

Another thing you could do is use gparted to delete your sda2 and sda3 partitions and create a extended partition as you can only have 4 primary partitions on a hard drive. Then recreate a ext3 and swap as logical partition. Doing this way allows you to have additional partitions in the future if you decide to.

---

### Post by ronparent on 2009-09-05
+1

Forgeting to set the mount point is an easy step to overlook (I've done it). Prorceeding as Partyboi2 has suggested would take care of the problem.

---

### Post by trojanworrier on 2009-09-06
Hi, when you get to the partitioning part of the install, choose "Manual" and edit your /dev/sda2 partition so that the mount point is set to / and that the partition is set as a ext3.
----------------
i didnt follow the above statement. from where could i choose "manual". i couldnt find it in gparted.

rather i chose to do with the following mathod you specified:
#############################################
Another thing you could do is use gparted to delete your sda2 and sda3 partitions and create a extended partition as you can only have 4 primary partitions on a hard drive. Then recreate a ext3 and swap as logical partition. Doing this way allows you to have additional partitions in the future if you decide to.
----------------
i made following partitions as per the above directions:

/dev/sda1 - ntfs  : 19.67 GB <-----windows 7
/dev/sda2 - extended  : 24.11 GB <-----
    /dev/sda5 - ext3  : 15.63 GB <----- linux ubuntu 9.04
    /dev/sda6 - linux-swap  : 8.48 GB <----- linux-swap
/dev/sda4 - ntfs  : 68.01 GB <----- DATA

no while installing:
i chose -- specify partitions manually(advanced) which led me to new window: "prepare partitions": i tried installing it "/dev/sda5" but i got a msg "No root file system is defined    please correct this from the partitioning manu"

please advice what should I do? should I install grub? i was trying to install grub again and used command "find boot/grub/stage1" but got a msg "no file found"

please advice. I really need help...
Thanks alot...

---

### Post by Partyboi2 on 2009-09-06
Choose "specify partitions manually(advanced)" then highlight /dev/sda5 and click on "edit" then set "use as" to ext3  and then set "mount point" to /

---

### Post by presence1960 on 2009-09-06
> **Partyboi2 said:**
> Choose "specify partitions manually(advanced)" then highlight /dev/sda5 and click on "edit" then set "use as" to ext3  and then set "mount point" to /

from the installer specify maual. see below screensht

---

### Post by trojanworrier on 2009-09-06
Thanks a lot Partyboi2, ronparent & presence1960. Finally, Ubuntu 9.04 successfully installed. 
Thanks...:popcorn:

---

### Post by presence1960 on 2009-09-06
> **trojanworrier said:**
> Thanks a lot Partyboi2, ronparent & presence1960. Finally, Ubuntu 9.04 successfully installed. 
Thanks...:popcorn:
Glad you got it working! Enjoy Ubuntu,

---

