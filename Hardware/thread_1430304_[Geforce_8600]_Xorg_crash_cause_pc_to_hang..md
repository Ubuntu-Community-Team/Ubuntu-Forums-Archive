---
title: "[Geforce 8600] Xorg crash cause pc to hang."
date: 2010-03-15
forum: Hardware
---

### Post by ScarFreewill on 2010-03-15
My brother and I installed Kubuntu karmic amd64 2 days ago. First updating apt (for latest kernel) after reboot we installed the latest proprietary drivers via jockey. Basically to sum it all up everything we try causes my brother's pc to lock up completely after KDM tries to boot with proprietary drivers. My brother ran 32bit 6.10-9.10 (x/k)Ubuntu and never had problems. The lucid tests were done in Xubuntu amd64 alpha3.

We struggled through the night spending two consecutive days trying every how-to we could fine determined to get the drivers working, alas no luck. We tried every driver from 173-195 on every kernel we could get from karmic to lucid, with over 50 different xorg.conf, drivers tested are both the deb's in normal repos, ppa:sevenmachines/nvidia for lucid's latest driver and then even trying the old nvidia.com run files (with all it's dependencies installed). Some posts made us very exited because we thought it was surly going to fix the problem, like [http://ubuntuforums.org/showthread.php?t=1330160](http://ubuntuforums.org/showthread.php?t=1330160) but at the end of the day we just learn some new commands ;).

Debugging is not easy since after the xorg crash I can't ssh to his pc to check dmesg. We monitored /var/log/Xorg.0.log but lost most of the feedback due to formating and reinstalling (not 100% about the best way to remove nvidia.com .run drivers, but I know formating helps :P).

I will try to get a Xorg.0.log asap, meanwhile is there anything else we can try? We live in South Africa international traffic is expensive, but if it's in the repos we can get it easily :D (not ppa repos though).

EDIT: attachment

---

