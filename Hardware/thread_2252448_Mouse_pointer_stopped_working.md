---
title: "Mouse pointer stopped working"
date: 2014-11-11
forum: Hardware
---

### Post by bizhat on 2014-11-11
On my PC mouse pointer stopped moving. Actually mouse itself is working, if i move mouse to a different location and right click, i can see right click menu comes up on different location.

After PC boots up, mouse pointer works (moves) for like 1 minutes, then it stop working. I tried Ubuntu 14.04 and Lubuntu 14.04, both shows same problem.

When this happens, i get following error message in dmesg

```

[ 2724.000012] [drm] stuck on render ring
[ 2724.000022] [drm] GPU crash dump saved to /sys/class/drm/card0/error
[ 2724.000025] [drm] GPU hangs can indicate a bug anywhere in the entire gfx stack, including userspace.
[ 2724.000028] [drm] Please file a _new_ bug report on bugs.freedesktop.org against DRI -> DRM/Intel
[ 2724.000031] [drm] drm/i915 developers can then reassign to the right component if it's not a kernel issue.
[ 2724.000034] [drm] The gpu crash dump is required to analyze gpu hangs, so please always attach it.
[ 2724.000821] [drm:i915_set_reset_status] *ERROR* render ring hung inside bo (0x535000 ctx 0) at 0x5351dc
[ 2724.512018] [drm:i915_reset] *ERROR* Failed to reset chip.

```

I tried different mouse/keyboard and USB ports. It do not fix the problem.

PC continue to work even after mouse pointer display stop moving.

Any suggestions on fixing this issue ?

---

### Post by mark180 on 2014-12-10
I have been experiencing exactly the same issue. It's almost always when I load some Youtube videos. Following advice from similar problems, I changed my X11 acceleration to UXA, but that didn't resolve the issue. I have yet to find a solution.

---

### Post by bizhat on 2014-12-10
I tried installing latest driver from PPA and also from Intel web site. That did not solved the problem.

Then tried installing Windows 7. I have too many graphics problem, it won't even finish install. That confirm it was due to a hardware issue. Hardware tech checked the motherboard said many capacitors are leaked (have visually bulged top). He take motherboard, replaced capacitors and it worked perfectly fine.

---

