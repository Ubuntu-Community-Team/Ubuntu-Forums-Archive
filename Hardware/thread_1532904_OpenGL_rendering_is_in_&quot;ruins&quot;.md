---
title: "OpenGL rendering is in &quot;ruins&quot;"
date: 2010-07-17
forum: Hardware
---

### Post by Dinchamion on 2010-07-17
Heya,

I have a Dell Latitude D610 laptop, which I know isn't a powerhouse, but for the things I need it it gets the job done. Or it did, until now.

I recently returned to Ubuntu from other distros, and I found that gaming, which was fine until now, became difficult, or in some cases impossible. I suspect it has to do something with the video driver (my laptop has an Intel 915GM card).

Some games work fine. But for example WoW crashes on startup when adding the "-opengl" flag or setting rendering to opengl in the config file, Syberia just shows a blank screen and Torchlight has broken rendering all over the place.

I did play WoW on this laptop for months before, so it's not a problem of the hardware.

Here is my glxinfo output:
```
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM GEM 20091221 2009Q4 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.7.1
```

My question is that does anyone has similar problems? Or is there a newer driver in the pipeline and I just have to wait for it? (Tried reverting to an older driver, but without reverting xorg-core as well it wouldn't install, and reverting to older (karmic) xorg-core broke X completely)

---

### Post by digitalcitizenx on 2010-07-17
I wouldn't say it is in "ruins" - but then again - I have well supported hardware.

At that - a little Google search revealed this link that may help your issue:

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)

Good luck and post back with your progress. It may help another user in the future.

---

