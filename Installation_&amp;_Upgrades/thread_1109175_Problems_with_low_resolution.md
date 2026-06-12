---
title: "Problems with low resolution"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by skinny.martin on 2009-03-28
H,

I've installed Ubuntu 8.10 and everything is working except that I cannot get a higher screen resolution then 800x600. The unicrhome driver is installed (xserver-xorg-video-openchrome) and my gfx card is via k8n800.

Any suggestions is highly appreciated.

Thanks,

Martin

---

### Post by WatchingThePain on 2009-03-28
I once had that problem and it was because  /etc/X11/xorg.conf never had all the resolutions listed.

---

### Post by skinny.martin on 2009-03-29
Thanks a lot. Now I can get higher resolutions... after wasting two whole days installing different drivers which made no difference. Its many years since I last tried using linux, and still such hardware problems can take ages for non-linux persons to solve...

However, in some resolutions I want to use the display the image is tilted to the left so that I cannot see everything, and my LCD screen is one without any manual control buttons... is there a way in which I can instruct the driver to tilt the image x1 no of pixels, and magnify x2 per cent in horisontal direction?

Thanks, now migration is on its way!

M

---

