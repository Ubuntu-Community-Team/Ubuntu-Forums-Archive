---
title: "Making an install CD with a custom kernel"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by dmallo on 2009-05-11
Hello all.

I'm trying to install Ubuntu server onto a system with two Western Digital hard drives. Unfortunately, the firmware on the drives is buggy, causing them to not be detected by stock Jaunty kernel. (This is a known problem, see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257790]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257790").) I have confirmed that the proposed kernel, 2.6.28-12, seems to fix the problem, by booting from a USB key.

In order to install the system, however, I'm going to need to customize the Ubuntu Server install CD, since its using the older, broken kernel. It's not clear to me, based on the guide at [https://help.ubuntu.com/community/InstallCDCustomization]("https://help.ubuntu.com/community/InstallCDCustomization") how to make a CD that boots the proposed kernel. :confused:

Any help here would be appreciated. Thanks!

---

