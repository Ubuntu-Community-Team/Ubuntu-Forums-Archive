---
title: "i915GM : glxgears too slow in Gutsy"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by coolos on 2007-10-21
Hello,
I've got a intel i915GM chipset in my laptop, and it seems that the default configuration in gutsy isn't optimal, ie in glxgears i use to have 500 fps (in box-window mode). It was the case in feisty (i810 driver), and also in sabayon3.4miniE liveCD.

But with gutsy, i only have 125 fps in glxgears (in livecd for example and it's the same after an install)
i checked glxinfo : it says "Direct Rendering : Yes"

Gutsy selects the default 'new' driver 'intel', but i have the same poor performance when i put the 'i810' driver in xorg.conf.

any idea to correct this low-fps problem in Gutsy ?

thanx !

---

### Post by daspooky on 2008-02-09
Incredible how dead these forums are sometimes...

I'm actually experiencing the same problem. My FPS are as high in glxgears as with the i810 driver (around 700 FPS), but I find application windows to render slowly (you can clearly see them redrawing with the "intel" driver), websites with lots of graphics are a pain to browse in any browser (100% CPU load),  javascript picture cross faders on some websites just render frame per frame (this worked normally and smoothly with the i810 driver).

I checked and direct rendering is enabled (but I have to say, I'm seeing no improvement compared to when it is disabled). It seems everything is rendered in software as the CPU hits 100% a lot of times...

So people, what the hell is going on with this "intel" driver? What is broken, and how can we fix it? 

I'm starting to believe coolos and me are the only ones experiencing crappy performance with this driver. I've been losing days of time on this issue, but the almighty Internet provides no solution.

Another thing: I could use the i810 driver + 915resolution to fix the issues, but firefox (yes only firefox) doesn't want to cooperate. There are graphical issues (jumping text en artefacts on moving objects) in Gutsy with this driver...

---

