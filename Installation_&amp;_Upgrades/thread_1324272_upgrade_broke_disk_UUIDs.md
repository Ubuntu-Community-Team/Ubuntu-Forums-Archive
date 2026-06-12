---
title: "upgrade broke disk UUIDs"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by decoherence on 2009-11-12
I've put Karmic on six computers now. The first four were flawless. The 5th flipped out during its first post-install bootup, claiming it couldn't find the home or swap partitions. Changing fstab to use the device names rather than UUIDs fixed the problem. I recall this happening on other Ubuntu upgrades. When I get home I'll use tune2fs to check the UUID of the drive and compare it to what is in /etc/fstab. Has anyone else seen this? Anyone know why the UUIDs broke? 

The sixth computer was the typical problem with Ubuntu where 'you can't get there from here' unless you have wired networking. Damn Broadcom wireless... That's another issue, though.

---

