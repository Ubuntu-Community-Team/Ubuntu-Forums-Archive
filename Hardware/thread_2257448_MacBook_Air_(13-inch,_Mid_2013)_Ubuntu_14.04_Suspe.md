---
title: "MacBook Air (13-inch, Mid 2013) Ubuntu 14.04 Suspend backlight Issue"
date: 2014-12-19
forum: Hardware
---

### Post by tomalperin on 2014-12-19
I've done a bunch of searching and can't find anything exactly like this other than a few users that may not have completely known the exact nature of the problem. This issue is on a Macbook Air 13, mid 2013, MacBookAir6,2. This model is a core i5 with Intel graphics.

The issue I am having is with how the backlight settings behave after the computer wakes from suspend. Before suspend the backlight behaves normally. After suspend, the backlight will either be at full on or completely off depending on where the backlight controls are set. at about 70 to 80% the backlight will toggle on/off. If the backlight is below the threshold it's easy to assume that the computer is locked up an only recoverable by holding the power button or using ssh to cause a reboot, assuming that it's been turned on since you must first unlock the screen by typing your password without any visual feedback before the brightness controls will work again.

This is not a complete failure of the brightness controls to work, however instead, it's that the backlight can only be either on or off after the first suspend since the last reboot.

---

