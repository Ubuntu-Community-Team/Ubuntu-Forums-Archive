---
title: "install partition problem"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by dandnsmith on 2009-03-15
I'm trying to install ubuntu 8.10 to an already partitioned HDD which has a free partition, and a linux swap partition already.

I don't get the option to pick the partitions, so lack the confidence to go ahead in a situation which might mess my existing setup (which has multiple OS of different flavours, and a lot of data of historical interest)

---

### Post by taurus on 2009-03-15
When you get to the partition screen, pick the Manual option and tell the installer to use whichever partition you have set aside for Ubuntu.  Don't forget to mount that partition to root and format it to ext3 or you will get an error message about no root partition defined.

---

### Post by dandnsmith on 2009-03-16
Thanks for that - I'll have another go.
It was getting the Manual option to pick the partition which seemed to give a problem, but perhaps another look will clear my head

---

### Post by dandnsmith on 2009-03-17
Managed to pick the desired partition, tell it where to mount it, and to format it - looks like the install process got confused by my tries at picking various options ans then going back ...

Now I'm sorting the whole mess out:
1)Installer overwrote my boot configuration, without so much as a by-your-leave - the older linux installs used to let you decide whether and where to install GRUB. I've recovered, thanks to a MBR backup made before, in anticipation.
2)Installer picked the partition *after* the one I selected (very carefully) and messed up the partition table by removing the record for the one I indicated - fortunately, the one it overwrote was OK for sacrifice, being a version of Vector Linux I tried a while back, but never really used.

---

