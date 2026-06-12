---
title: "headless machine screen resolution problem"
date: 2008-08-19
forum: General Help
---

### Post by jharadie on 2008-08-19
Hi, trying to set up a headless machine for secondary purposes, controlled through primary machine via remote desktop.  Installed 8.04 alternate on Microtel 1.6G CPU, 768RAM, using Westinghouse LCM-17v2-SL flatscreen monitor.  Wonderful resolution, lowered it to 1024x768 by choice.  Vino worked great.  To my knowledge, there's no NVIDIA in play (locate NVIDIA produced no results).  BUT, when I turned off, unplugged monitor, restarted and vino'd into it, resolution changed to 960x600 and that was the max.  Reattached the monitor, and got my great resolution back.

Forum searched X11, Xorg, and gdm, but I'm still enough of a noobie that, while I saw a lot of code, I didn't understand it, and couldn't find anything in noobie language. :)

Currently, my xorg.conf file (with monitor attached) says

Section "Device"
     Identifier     "Configured Video Device"
Section "Monitor"
     Identifier     "Configured Monitor"
Section "Screen"
     Identifier     "Default Screen"
     Monitor     "Configured Monitor"
     Device     "Configured Video Device"
Section "Server Layout"
     Identifier     "Default Layout"
     Screen     "Default Screen"

Is there somewhere else I should be looking/tweaking?  I really need this machine to be headless, but keep the 1024x768 resolution.

Thanks.

---

