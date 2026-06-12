---
title: "Upgrade from Intrepid to Jaunty Disk Space issues"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by kendoori on 2009-08-23
I have a box that I use as a NAS that has 8.10 installed on a CF card. When I tried running the stock upgrade process to 9.04 the process crapped out complaining that there wasn't enough disk space. I tried doing a bunch of pruning and removing various packages to no avail. 

Gparted says that I have 1.02 GiB left (Disk Usage Analyzer disagrees and says I have 814.2Mb left)... either way, the 9.04 script won't work when run from within the working install. I would prefer to not have to start from scratch as the box is configured per my needs and I'm not much of a power Ubuntu user.

Is there a means of easily preserving my configuration and upgrade?

---

### Post by stlsaint on 2009-08-23
granted there are many ways but you didnt provide much info so i would recommend doing a backup of /home...then upgrade and restore!

---

### Post by slakkie on 2009-08-23
Please have a look at the following thread:
[http://ubuntuforums.org/showthread.php?t=1238309](http://ubuntuforums.org/showthread.php?t=1238309)

Some pointers in how to remove files which are not needed anymore.

You could also install the following package 'localepurge' which will remove unneeded locale files (language files) from packages. Could save you some additional space.

---

### Post by kendoori on 2009-08-24
I tried localpurge and many of these techniques, but I still appear to be about 400MB short on space. Would it make any difference to trigger the upgrade somehow from an ISO or CD. 9.04 probably takes up more room than 8.10, but is my problem the fact that during the upgrade process, one has to deal with the fact that there needs to be enough space to temporarily accomodate the space needs of the existing install + the packages of 9.04?

---

