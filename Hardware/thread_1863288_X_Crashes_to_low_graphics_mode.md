---
title: "X Crashes to low graphics mode"
date: 2011-10-17
forum: Hardware
---

### Post by m0jo1337 on 2011-10-17
Hi,
im encountering this erorr and google didnt help so far:

It does not seam to happen on a certain event, but mostly when i start an application (Often Chromium, sometimes some others when using wine). It says something like this:
intel(0): Input/output error

And brings me to an option page (in low graphics mode) where i can choose whether to restart X, drop to shell session or to debug the rror.

X.org log says at the end: 

Fatal server error:
Failed to map batchbuffer: Input/output error

[Xorg.0.log]("http://pastebin.com/X9uHYfwg")
[Xorg.1.log]("http://pastebin.com/vU3XHHwP")

Can someone please help me? It is recently happening quiet often (once a day / 2 days).


Thank you in andvance!

---

### Post by PsyGeek on 2011-10-17
I had a quick look, but I know very little about hardware and hardware issues. I assume there is something wrong with your video drivers. You have the same graphics chipset as me:

(II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
(--) intel(0): Chipset: "GM45"

As far as I know, we need the normal intel video drivers, so I would (re)install xserver-xorg-video-intel. Also, the first log complains that the font cyrillic isn't installed, so you should probably reinstall those (xfonts-cyrillic) as well.

In short, try this and if nothing improves hope that someone with a better understanding of hardware and logs takes a look :):

> sudo apt-get install --reinstall xserver-xorg-video-intel xfonts-cyrillic


or just to be certain (all instead of intel):

> sudo apt-get install --reinstall xserver-xorg-video-all xfonts-cyrillic

---

### Post by m0jo1337 on 2011-10-18
I did what you said and also installed a new Kernel (*2.6.39-020639rc4-generic*)


I'll report if I encounter that error again.

Thank you so far!

---

