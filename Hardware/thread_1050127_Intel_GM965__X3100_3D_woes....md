---
title: "Intel GM965 / X3100 3D woes..."
date: 2009-01-25
forum: Hardware
---

### Post by sakus on 2009-01-25
Ok so I've been reading about the GM965 chip problems but was just wondering if my problem is related to that or something else.

I seem to have 3D acceleration working but most things 3D doesn't work.
The laptop's an Acer Aspire 5315 with the dreaded Intel GM965. 

```

glxinfo | grep direct
direct rendering: Yes

```

```

glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM 20061102 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.2
OpenGL extensions:

```

glxgears reports ~750fps
Compiz works.
OpenGL screensavers work.
Google Earth starts to show the globe for half a second, then crashes.
Tux Racer crashes as soon as you try to advance from the menu, Scorched 3D works on failsafe settings only. Anarchy Online under Wine (what I'd like to mostly use this laptop for) starts up but the screen stays black.

Having Compiz on or off doesn't make a difference.

Using Ubuntu 8.10. Just poor Intel drivers to blame? There seems to be way newer version available, is there maybe a 3rd party repository somewhere I could add to pull in newer drivers? Or pulling in unstable packets or something? I'm new to Ubuntu but not to linux in general, but I'd rather not install anything bypassing the package manager if possible (although I already had to install madwifi manually to get wireless working).

---

### Post by Sam Lars on 2009-01-25
I too have had issues with the Intel, believe me, you're not alone.
If you want to try the testing version of the driver, it's here:
[https://launchpad.net/~intel-gfx-testing/+archive](https://launchpad.net/~intel-gfx-testing/+archive)
I can't say it's much better, but at least it's newer.
Disabling Compiz should help a lot, though.  How are you turning it off?

---

### Post by sakus on 2009-01-26
I just simply chose "no effects" or something similar in the appearance settings, judging by what it seems to do it seems to switch the compiz wm off completely and start using the default gnome one instead of just turning all compiz effects off. Or should I try something else to make sure compiz is not in use at all?

Thanks for the link, I'll try it once I get home from work. Although it seemed to me that there's only version 2.5.1 in there? [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/) has 2.6.0 out as well, released earlier this month. Maybe I was just reading it wrong, I'll find out at home.

---

### Post by Sam Lars on 2009-01-26
From what you said, it seems that Compiz is off.
If you want to try building Intel's 2.6 from source, you can try that.  I'm not sure when the PPA will follow with the new version.

---

### Post by sakus on 2009-01-27
Tried a newer driver from the link you gave, no noticable differences.

I'll try to build from source today I think, see if the newest one works any better (if I get it to work at all that is).

---

### Post by Sam Lars on 2009-01-27
They just posted a package of the new mesa driver on the [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/146298").

---

### Post by mttman on 2009-03-30
Hello everyone,

I'm wondering if there is a package for the 2.6.x intel drivers somewhere, I'm currently running the launchpad drivers which are version 2.5.1 but it hasn't fixed the problems i'm having with 3d games (both native linux and windows games under wine) Compiz is working correctly, my glx gears gives me about 300-350 fps (something i'm a little worried about seeing how others get 700+). i know you can download and compile them but i've always been very cautious about doing that with regular programs much less with drivers. 

Thanks for anyones help

Mttman

---

