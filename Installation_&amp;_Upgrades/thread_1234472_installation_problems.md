---
title: "installation problems"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by chchew90 on 2009-08-07
now i wants to using dual boot with vista and ubuntu. then after i download, i install the ubuntu but from last nite until now the installation havent finished yet,what is the problem?some one told me the installation only took for less than half an hours. and I choose to save it in D: partition, coz my laptop have two partitions. In the D: partition, i found 3 floder named:disks,install and winboot. then have two icon, one named ubuntu and one is uninstall. is it means the installation have already finished?but the installer still stop at the same place and din show that it is finished, what to do?

---

### Post by presence1960 on 2009-08-08
after you download the Ubuntu iso you need to check it with [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM"). Then you need to burn the iso to a cd as an image, if you don't know how to do that see [here]("https://help.ubuntu.com/9.04/switching/installing-burning.html"). Burn the CD at a slow speed- 4x is good. 

Next you need to shrink Vista's partition from within Vista to create space for Ubuntu. Use vista's disk management utility to do so. it would be wise to defrag Vista at least once or twice prior to doing so.

Then you need to make sure your machine is set to boot from a CD. Go into BIOS and ensure that the first boot option is CD. Then boot off the live CD and proceed with the install.

If you don't want to partition your disk, try [wubi]("https://help.ubuntu.com/community/Wubi"). I don't recommend wubi as anything other than a test drive. it is not meant to be a permanent solution.

---

