---
title: "Video issues with laptop"
date: 2009-04-12
forum: Hardware
---

### Post by magh-87 on 2009-04-12
Hey,

I'm using an Acer TravelMate 2420, Intel Pentium M 735A, Intel Graphics Media Accelerator 900, 1GB RAM, 100GB HDD.

The issue is whenever I watch a video on my laptop, the video is laggy/choppy and not in sync with the sound.

I've been searching google and the forums all afternoon trying to find a solution to this. I'd really love some help on this.

Thanks,

Magh

---

### Post by mvdberg112 on 2009-04-12
My video is not choppy, but sometimes the sound is say about 0.5 sec late. I attribute that to the source-video, although it is strange. Does flash (if you use flash to watch that video) use some buffering, which is out of sync?

Choppy video usually is caused by too slow hardware/software mix or by not-correct functioning video accellaration.

Try to find out with 
# top 
if there is an application that uses too much processor power or too much memory (causing swapping). Both might not be an issue, or top might not show it, but it is easy to check.

---

### Post by magh-87 on 2009-04-12
The only thing that appears to be eating up any resources is firefox, which is what I'm using to try and watch most of these videos. Everything is up to date on my computer. I am using 9.04, if that makes a huge difference right now. I'm still quite new to this.

Magh

---

