---
title: "Multi-display configuration fail &quot;Size out of limit&quot;"
date: 2011-10-14
forum: Hardware
---

### Post by cwestpha on 2011-10-14
I just performed a fresh install of 11.10 for my 2008 MacPro with the standard AMD GPU drivers for the BARTS line (Radeon HD 6870). I tried the post-release drivers, which failed, and was able to get the standard release drivers working just fine. However, when I rebooted I find I am unable to set anything other then a cloned display setup for my two displays. I have tried using the desktop utility and setting both 1:1 screen resolutions (1680x1050) and both native (1920x1200 & 1680x1050) with both giving the following error:
"The selected configuration for displays could not be applied. requested position/size for CRTC 64 is outside the allowed limit: position (=1280, 0), size(1920, 1080), maximum=(1920,1920)"

Furthermore I tried using the AMD utility included with the drivers to no effect. When I hit apply the utility just closes with no changes made.
With 11.04 I was able to just set a virtual resolution of 3600x1200 and it behaved that way (despite losing a bit of displayed space due to the virtual desktop being larger then the physical desktop).
Any ideas how to fix this in 11.10?

---

