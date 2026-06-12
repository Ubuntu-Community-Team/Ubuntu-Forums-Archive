---
title: "New gfx card"
date: 2008-06-27
forum: Hardware
---

### Post by ProbablyX on 2008-06-27
Hi!

Ive just upgraded form a 8600GT [nvidia-glx-new driver] to a 8800GT.

As the upgrade ruined X I followed another post, reconfigured the xserver with dpkg and removed the drivers, replacing them with the envy ones.

I however have some problems. My keyboard layout is english, I had Swedish before, and my alt and altgr buttons arent working.

I expect I can just copy the keyboard data from my backup xorg file, but is there any additional stuff I should add there? I mean after the upgrade and so on.

Another question too: GLXGEARS reports ca 4500FPS for my card. That looks very low for a 8800GT. Im running KDE4 with compositing features though. The fades and desktop effects work fine, so maybe KDE is eating the card's performance. What is a normal glxgears output?

Thanks! :)

UPDATE: I just found that the Xorg file did have a line saying "us" for they keyboard settings, changed it to "se" and now my keyboard works again (alt too).

---

