---
title: "Install error?"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by fcbhuss on 2009-10-22
Hello all...I attempted to install Ubuntu 9.04 several times, with partial success.  After loading about 20+%, I'd then get [error 5] something or other.  Basically realized the boot disk had an error.  Burnt new disk, installed Ubuntu no problem.  However, once installed, I realized I had 3 partitions...one 2.5GB, one 20GB and one 23GB.  It appears the operating system is on the smallest partition and I can't use the update manager because its essentially telling me I have no free space.  Is there a way to switch to one of the larger partitions (I tried the Partition editor to expand the small partition but it won't let me add to the 2.5GB partition)???  Or is there a way to uninstall Ubuntu and do it from scratch now that I know I have a good boot disk?  :confused:  
Any insight is very welcomed!!!!  Thanks

---

### Post by dominiquec on 2009-10-22
You could use gparted to resize the partitions, but I think that's more trouble than simply reinstalling, especially for a new system.

---

### Post by fcbhuss on 2009-10-22
I'm thinking reinstalling would be the best option also.  When I threw the boot disk in to look at reinstalling, it shows that I have Ubuntu on my hard drive 3 times (the 3 partitions of 2.5GB, 20GB and 23GB).  So if I reinstall as is, I'd have 4 of them on there.  I guess my real question is how to get rid of the 3 old installs and just have one Ubuntu of 45GB on my hard drive.

---

### Post by revanb on 2009-10-22
You should choose the > Use whole harddrive < option during the install process. I'm not sure of the wording, but that's what it boils down to.

Also this option will format your whole drive, so you shouldn't have data you want to keep unless its backed up.

---

### Post by fcbhuss on 2009-10-22
Thanks for the feedback but unfortunately I left off one piece of info....'m doing a dual boot with XP.  My wife isn't as ready to loose the training wheels of Microsoft, so I'm leaving XP on there for now.  That is one wrench in the works that I'm hoping to work around.

---

### Post by fcbhuss on 2009-10-22
Problem solved, here's how - I used the Partition editor to resize/move things around the partition with the operating system.  The hangup I had before was that since that partition was mounted, I couldn't resize it.  My buddy suggested I put in the boot disk and run the test out Ubuntu mode.  Once I did that, I then went into the partition editor.  Since I was running off the disk vs the partition, it was now unmounted and able to be resized.  Added all the excess space I had created before and now have a fully functioning system.  

:guitar:

---

