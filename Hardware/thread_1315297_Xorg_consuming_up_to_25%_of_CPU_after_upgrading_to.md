---
title: "Xorg consuming up to 25% of CPU after upgrading to 9.10"
date: 2009-11-05
forum: Hardware
---

### Post by manolomanolo on 2009-11-05
Hi to all.

I'm trying to collect people experiencing my same issue after upgrading from Ubuntu 9.04 to 9.10 (stable)

That's the bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/472406]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/472406")

Thanks for your attention.
Regards.

SOLVED: for some reason, during the upgrade, the kernel was not updated. Updating the kernel and grub2 solved the problem.

---

