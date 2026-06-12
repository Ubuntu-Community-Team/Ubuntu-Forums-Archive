---
title: "New Install Help"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by josh_moore on 2009-10-24
So I am still very new to Linux, but I've decided to get rid of Windows on my main system (already running UNR on my netbook and loving it)

For my Windows setup I had two 640gb hard drives, using my onboard Gigabyte RAID these were setup in RAID0. As I understand it Linux does not support driver/host based RAID, I am just as content to use software RAID with Linux, the question is how.
I have already broken the previous RAID0 and set the drives as no-raid within the controller, on booting to Ubuntu 9.04 the partitioner starts and I can see both drives, but no options other then to partition the drives individually.
After searching I found the following article
[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

However one of the steps indicated here fails, after installing lvm2 in the LiveCD enviornment,
$ sudo modprobe dm-mod
FATAL: Module dm_mod not found.
I honestly do not know what this is suposed to do, but continuing with the guide, modified for my setup, when I start the install the lvm shows as unknown for filesystem. It seems to me that the install is not loading LVM support.

Any help on this would be greatly appreciated, in the end I simply want a software RAID0 or functional equivilent across my two hard drives

---

