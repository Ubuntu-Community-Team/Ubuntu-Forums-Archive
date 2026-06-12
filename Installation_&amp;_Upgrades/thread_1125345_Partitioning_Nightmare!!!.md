---
title: "Partitioning Nightmare!!!"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by smurfyboy88 on 2009-04-14
I have recently made a UBUNTU LiveCD and have decided to install the OS from it. However, as i reach the installation step on which i must partition my hardrive, i have run into problems. I am given no option "Guided - resize the partition and use the freed space."

I already use Windows XP and would like to create a dual-boot set up. My laptop has a 65GB hardrive and 1GB RAM.
I do not want to lose any files that I already have.
Thanks

---

### Post by sesheron on 2009-04-14
If you are needing to shrink the windows partition in order to install linux there are a few things you need to do first.
The ubuntu installer itself won't shrink a partition.  But the tools you need are on the disc.
First go back into windows and do these things
-Defrag
-Empty Recycle Bin
-Backup data
-See just how much free space you have
Now in the Linux live cd, under the administration options there is a Gparted or something similiar.  This tool will shrink the windows partition, but make sure to leave some free space for breathing room.
Then format the newly created second partition to something basic and go back into the Ubuntu installer.

But if I were you google something like "howto shrink and dual boot windows ubuntu" and find a nice guide with more detailed steps.

---

### Post by Elfy on 2009-04-14
The livecd will in fact resize the partition. But as sesheron says defrag a couple of times first.

---

