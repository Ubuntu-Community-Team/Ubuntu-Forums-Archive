---
title: "weird bootup issue on dual monitors (link to video)"
date: 2010-12-08
forum: Hardware
---

### Post by moderemx on 2010-12-08
Hey guys. I've installed Ubuntu 10.10 on every computer in my house without any problems except my laptop. I don't use the laptop LCD (max resolution is 1024x768 ) as I have an external display (1920x1080) so in Ubuntu I turned mirroring off and then the laptop display; applied, then set as default. Now during boot up Ubuntu sets the resolution to 1920x1080 but shows the background tiled as if it were set on the 1024x768 resolution.

When mirroring was enabled, the highest resolution I was able to select was the the maximum the laptop LCD could handle (1024x768 ). I'm guessing that if I could prevent Ubuntu from recognising that monitor it would eliminate the problem. Unfortunately, the BIOS doesn't contain an option to disable it. I also do not have a /etc/X11/xorg.conf file and last time I tried creating one it didn't have any positive impacts.

Although it's a minor cosmetic issue, it's annoying. Any ideas?

[View Video]("http://tinypic.com/r/kaii4i/7")

---

### Post by Fafler on 2010-12-09
Pretty boring video :-)

So, the background is 1024x768 for a few seconds and then changes to 1920x1080? Try having using a background image that is native 1920x1080.

---

### Post by moderemx on 2010-12-09
Sorry, wasn't enough budget for all the special effects.

I tried using 1920x1080 and larger images with no luck. Ubuntu comes with higher resolution photos too.

I believe this is causing the icons in my top panel to rearrange. Every time I boot or reboot, it rearranges. (I found a way to reset it by searching on Google).

I'll try any suggestions thrown

---

### Post by Fafler on 2010-12-09
The only other thing i can think of is to disconnect the LVDS cable inside the laptop.

---

