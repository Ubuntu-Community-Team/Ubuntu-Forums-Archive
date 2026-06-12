---
title: "Trying to anticipate problems that may arise from moving hard drive to new hardware"
date: 2015-10-11
forum: Hardware
---

### Post by stevecro2 on 2015-10-11
Because of some erratic POST light behavior on my Dell Dimension, I think I may soon be having to either a) replace a motherboard, or b) move my hard drive (which has 3 bootable Linux partitions on it -- 2 versions of OpenSuSE and 1 Ubuntu -- and multiple GRUB's) to another new machine/case/motherboard/processor. Before I do this, would like to get an idea of what problems I may have. 


The first one that comes to mind is that the current computer has NVidia video and the new one might have something different. (Boot up in a video failsafe mode and download whatever different video driver I might need?)


What other problems might I have? Startup only fails intermittently so far, so not yet an urgency, but I just want to think about how Ubuntu might react before I go to my local shop and get this replacement done.

---

### Post by efflandt on 2015-10-11
Have you checked **dmesg** or any logs in /var/log to see if there are any drive issues. Although, if there is a drive problem and Linux remounts your drive read-only to protect it, that may not be logged. Install **smartmontools**  if you do not have it and see what **smartctl** says about your drive.

Before (or maybe even after) moving the drive, you could boot a (recovery) kernel from grub and remove nvidia drivers if the new computer does not have nvidia or has a new nvidia chip that might need a newer driver installed from graphics-drivers/ppa. From the recovery menu that comes up enable networking which also remounts the drive from read-only to read-write and wait until it returns to the menu if there are any messages about unidentified hardware. Then go to root console (since you are root it does not matter if you use sudo like you would normally need for these commands):```
apt-get purge nvidia*
apt-get autoremove
```If you were using xorg-edgers/ppa, that no longer has video drivers, so you should **apt-get install ppa-purge** if you do not have it and then **ppa-purge ppa:xorg-edgers/ppa** (note that you would normally need sudo prefix if not in root console).

Then if you have a newer nvidia chip (especially 900 series, maybe 800M series too) you could add the graphics-drivers/ppa, then **apt-get update**, then if running Ubuntu 14.04 or 15.04, **apt-get install nvidia-355** (which works for my GTX 765M and GTX 750 Ti), or nvidia-352. Newest there if still running Ubuntu 12.04 is nvidia-346. Then **reboot**. More info: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

While I still have a old Celeron 333 PC in my basement that has been  running SuSE 8.2 24/7 since 2003 as an experiment, I don't know if  current SuSE still uses yast2 or how that works because 8.2 has been  obsolete for many years.

---

