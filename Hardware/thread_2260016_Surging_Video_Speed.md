---
title: "Surging Video Speed"
date: 2015-01-08
forum: Hardware
---

### Post by mcman56 on 2015-01-08
When playing MP4 videos, the video speed sort of surges with an uneven speed.  This happens in Videos and Openshot Video Editor.  VLC was very bad.  It happens on videos from a GoPro and from a security DVR (both 1080p) running from the camera, USB or hard drive.  After starting to play, audio only works for a few seconds on the GoPro video.  I tried different video drivers with no affect.  [FONT=&quot]The videos work fine in Quicktime on a Vista PC with a 2.5GHz processor. (6gb memory, 64 bit). The specs for the Ubuntu machine show an AMD Dual Core Processor E1-1200 with a speed of 1.4 GHz and an [/FONT][FONT=&quot]AMD Radeon HD 7310 video card.  

Could there be a fix for this?
[/FONT]

---

### Post by kerry_s on 2015-01-08
just a wild guess, but perhaps 1080p is just to much for that processor to keep up.

---

### Post by mcman56 on 2015-01-08
That is one concern but I wonder if more RAM will help video speed.  A web search suggests it may help video speed in some situations but I don't know if it fits here.  This has 4GB.

---

### Post by kerry_s on 2015-01-08
> **mcman56 said:**
> That is one concern but I wonder if more RAM will help video speed.  A web search suggests it may help video speed in some situations but I don't know if it fits here.  This has 4GB.

i doubt it, it's the cpu that counts, it just can't process fast enough to keep up. i doubt your even using half the ram you have now.

in the past, what i would do is select a media player that you could set the buffer on, it would take a while to start the movie but since the cpu had a head start it could stay ahead & play smooth.
try vlc or gmplayer.

---

### Post by mcman56 on 2015-01-08
System details are attached.  Is a dual core 1.4 mhz equivalent to a single core 2.8 mhz?

AMD E1-1200 APU with Radeon(tm) HD Graphics × 2 

AMD Radeon HD7310

It was used in a number of systems.
[http://www.ubuntu.com/certification/catalog/component/dmi/4458/dmi%3AAMDE1-1200APUwithRadeon%28tm%29HDGraphics/](http://www.ubuntu.com/certification/catalog/component/dmi/4458/dmi%3AAMDE1-1200APUwithRadeon%28tm%29HDGraphics/)

[http://www.cpu-world.com/CPUs/Bobcat/AMD-E%20Series%20E1-1200.html](http://www.cpu-world.com/CPUs/Bobcat/AMD-E%20Series%20E1-1200.html)

---

### Post by kerry_s on 2015-01-09
i thought it was just a single core, dual core should handle 1080p just fine.
it must be some kind of driver issue.

---

