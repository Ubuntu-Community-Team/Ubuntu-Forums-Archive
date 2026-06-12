---
title: "No disc space / after install"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by banzairx7 on 2009-06-30
I'm trying to install Ubuntu along side windows XP. Seems no matter what I do after ubuntu installs it says it has zero room left on the drive. First I installed ubuntu along side windows- no space left on drive. Then partitioned windows by itself using 70gb for XP, 1gb for swap, 9gb for ubuntu /. Still no room on drive in Ubuntu. Then I did no swap file and allocated the entire 10gb to /. Now I have 36mb free in ubuntu. Windows is using its 70gb partition with zero problems. How the heck do I install this so Ubuntu has hard drive space to use??

---

### Post by drs305 on 2009-06-30
You can try booting the LiveCD without installing to get to the Desktop, where you can run gparted (System, Administration, Partition Editor) to see if the drive is partitioned the way you think. The initial install shouldn't take up anywhere near 9GB of space. 

You can also visit this link to view a tutorial I wrote about how to check your disk and find out where all the free space has gone. In your case though it is probably something on the initial install rather than extra files being formed after the installation. 

[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

---

