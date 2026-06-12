---
title: "intel i915 jaunty -- no /dev//dri/card0"
date: 2009-06-23
forum: Hardware
---

### Post by syrex314 on 2009-06-23
I realize much has been posted on this topic, and I have been wading through forum posts for the last hour and a half, so please forgive me if my issue has been resolved elsewhere.

Upgraded to Jaunty on my eeepc 1000HD, found that compiz no longer worked. Suspected something was wrong with DRI, started walking through [the intel performance troubleshooting guide]("https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance").

I found /dev/dri is missing entirely. Reloading i915 (rmmod i915; modprobe i915) does not fix this problem. After modprobe 915, /var/log/messages reports no errors:

Jun 23 09:48:57 genesis kernel: [  280.410704] [drm] Initialized i915 1.6.0 20060119 on minor 0

Is something broken with udev?

---

