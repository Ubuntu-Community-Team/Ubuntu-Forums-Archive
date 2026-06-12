---
title: "Dynpm in rc.local"
date: 2011-03-08
forum: Hardware
---

### Post by NathanKell on 2011-03-08
I have an nc8430, and I finally have Radeon KMS power management working by command, following this guide:
[http://www.overclock.net/linux-unix/731469-how-power-saving-radeon-driver.html](http://www.overclock.net/linux-unix/731469-how-power-saving-radeon-driver.html)
(Note that, annoyingly, putting radeon.dynpm=1 in grub, unlike earlier kernels where that's necessary, breaks KMS in 2.6.35--took  a long time to figure that one out).

However--and hence my question--adding the line to rc.local doesn't work. On a fresh boot, when I cat power_method, I get profile. I can then sudo and echo dynpm, and it sticks, but I want this done automatically.
Is rc.local for some reason not executed as root? Or is it executed before /sys/class/drm/card0/device/ is mounted, or does something else run afterward to reset it to "profile"?

Or is there another way to automatically run a few bash lines as root, after everything else? Some gnome startup script I can edit?

Many thanks!

---

