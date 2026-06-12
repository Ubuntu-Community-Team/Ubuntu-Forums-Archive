---
title: "Xorg consuming up to 25% of CPU after upgrading to 9.10"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by manolomanolo on 2009-11-05
Hi to all.

I've opened a new bug report on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/472406]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/472406")

Please join to that bug report page in case you experience the same issue. Please try to describe your problem in detail.

Thank you.

**SOLVED**: for some reason, during the upgrade, the kernel was not updated. Updating the kernel and grub2 solved the problem.

---

