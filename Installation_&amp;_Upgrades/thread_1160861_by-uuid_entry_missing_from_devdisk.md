---
title: "by-uuid entry missing from /dev/disk"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by pohamala on 2009-05-16
Hey,

I've been trying to get udev working properly w.o. success. The problem is that under /dev/disk I've only by-id/ and by-path/ sub-dirs, by-uuid/ is missing.

My setup is the following:
- Currently on 8.04 with latest updates
- AMD64
- nvidia 1+0 raid with 4 identical disks
- dmraid

I've tried 8.04, 8.10 and 9.04 with identical results, no by-uuid entries. So the first obvious question is: should udev create by-uuid entries at all when dmraid is installed and disks are actually behind /dev/mapper/nvidia... structures? If it should then what goes wrong?

With live-cd's I've been able to detect the following behavior:
- live-cd up normally, at that stage there is no dmraid so all disks are under /dev/sd(a|b|c|d). udev does not create by-uuid's at all
- when dmraid is installed from multiverse by-uuid's appear as well mapping properly from /dev/mapper/nvidia towards corresponding uuid's
- but when newly installed system is booted the uuid's are gone again.

So, the system is stable as I can work with /dev/mapper/nvidia... notation on my configuration. But it is still a bit annoying not to have uuids present.

Any advice on how to proceed? Placing a bug towards 8.04, 8.10 and 9.04? For dmraid or for udev (probably for udev)?

Br
  Pekka

---

