---
title: "External Monitor plugged in after startup (Hardy 8.04)"
date: 2008-07-13
forum: Hardware
---

### Post by chickendude1313 on 2008-07-13
Hello,

Is there a way to configure such that I am able to plug in my external (1680x1050) VGA monitor AFTER start up and get that resolution.

Currently, if I plug in the VGA monitor afterwards, its stuck on the laptop's old resolution of 1280x800.

xrandr -q shows that max screen resolution is only 1280x1280
If the VGA is plugged in at startup, then  the max is 1680x1680

I need to dynamically set the max resolution, or just have it set to 1680x1680 regardless.

Editing the xorg.conf file and restarting causes X to give me an error forcing me to run in low resolution (800x600).
Hardy's xorg.conf is so useless.

---

