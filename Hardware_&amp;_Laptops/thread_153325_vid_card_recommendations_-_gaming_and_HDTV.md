---
title: "vid card recommendations - gaming and HDTV"
date: 2006-03-31
forum: Hardware &amp; Laptops
---

### Post by hotani on 2006-03-31
I'm building a machine and am having a hard time telling the difference between the various cards out there. Even limiting my search to nvidia still returns tons of results (7300, 6800, 7600, 7800, etc....) and I wanted to get some real world feedback about how these are working under linux.

One question is really standing out: what do they mean by HDTV? Most cards I looked at support resolutions far and above what would be considered HD - doesn't make much sense that one would be labeled different from another.

I have a 37" LCD (DVI) that runs 1920x1080p - it *is* an HDTV but I'm also using it for my primary monitor. I need a card that will:
A) output smooth video at full 1080p via MythTV or Mplayer
B) work well for whatever FPS games I can find to play on linux, at 1920x1080 preferably.
C) fit my 200-ish price range. They get up to $300 pretty quick I've noticed, but then I'll find a card with similar specs for $100 - thus the confusion.

I'll be running an AMD 64 X2 CPU, most likely the 3800.

---

### Post by Jason_25 on 2006-03-31
I think you should look into at at least a 6800 ultra/gs to play at that resolution.  What 1080p movie formats do you have that will playback in linux right now?  The only thing I can think of is WMV HD, which because of the drm most titles use, will not work in linux, and even if it did, there would be no hardware assistance to play it back from the video card.  As for H.264, I don't know about that.

---

### Post by hotani on 2006-03-31
Just thinking about the future for 1080p playback (very hopefully and in an ignorance-is-bliss sort of way...). 

This will most likely be a MythTV box as well as my primary PC, so I could be watching quite a bit of 1080i content once I get that set up.

I found [this 6800GS](http://www.newegg.com/Product/Product.asp?Item=N82E16814130267) over at newegg - seems to be a relatively good price. Any issues with driver support on ubuntu?

---

### Post by Jason_25 on 2006-03-31
That card looks great.  It should be a screamer. According to [this]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-a.html") page, it is supported on the latest version of nvidia's linux driver.  If you use breezy, you'll have to find a way to install the driver, or just update to the dapper drake.

---

### Post by Schmung on 2006-03-31
The 6xxxx series and up support hardware accelerated decoding of certain content (h264 I think) and are generally pretty meaty cards. No idea of what linux support for them is like aside from my own personal experience with my 6800GT, which has worked flawlessly.  As for specific support for certain things within Linux, I've no clue and I fully imagine DRM will be an issue of sorts. I just know what the hardware is capable of in windows and in hardware. I'd reckon a 6800GS would do you just fine.

---

### Post by hotani on 2006-04-01
thanks for the comments - i'll move that card to the top of the list. Good to know it is supported, I'll figure out the *getting it to work* part when i install the system I suppose.

---

