---
title: "xserver-xorg-video-intel bad opengl performance"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by MaximusTG on 2007-06-21
On my laptop, an Acer 3680 with Intel gma 945 graphics chipset, I had the xserver-xorg-video-i810 package installed. It performed reasonably well in Beryl. When I ran glxgears it gave me around 800 fps. Direct rendering was reported as yes. So then I read that the xserver-xorg-video-intel driver was newer, and didn't needed the 915resolution hack to work with widescreen. I installed the intel driver, and edited my xorg.conf. Restarted the Xserver, and it all seemed to work. However, when I rotate my desktop cube, when a workspace has only 1 Firefox window open, the framerate seems to go down a lot (very choppy) and CPU usage goes to 50-60% (celeron M 1,5 GHz). 
Is there some option I have to enable or disable in my xorg.conf, or am I stuck with the i810 driver?

---

