---
title: "Stability problems only with NVIDIA GT 630 (2GB VRAM)"
date: 2013-09-05
forum: Hardware
---

### Post by flix3 on 2013-09-05
Hello everybody!

I'm a new user of this forum (this is my first post here), but I started using Ubuntu (currently version 13.04 64 bit) two or three years ago.

I got a very strange stability (?) problem.

Every now and then I got Input/Output errors: I cannot open many folders on my HD, I cannot save files, 
I cannot even shutdown down the PC (I have to power it off)  (*).

However the PC is usually not completely locked (I have some error "message boxes" inside Nautilus when I try to access most of my PC folders: these message boxes say that there are Input/Output errors in accessing some specific paths).

I suspect that it depends on my NVIDIA graphic card change: I replaced a GT120 (1GB vRAM) card with 
a GT630 (2GB vRAM) when the problem started to appear (I've kept the same video driver I had installed with the old graphic card (310.44): maybe that's the problem; but the NVIDIA control panel correctly detects the new video card).

I've tried switching it back to the old GT120 and the problem never showed up again. 
How can this problem be somehow related to the video card ?

(*)- In unix shell I've tried to call 'shutdown' and the answer was: input/output error.

---

### Post by flix3 on 2013-09-19
I've ended up reinstalling my GT120 and throwing away the GT630 card.
The problem never showed up again.

It's probably due to a hardware problem in my Gigabyte GT630 card, or maybe it is not compatible with my motherboard (an old Gigabyte model).

Problem solved.

---

