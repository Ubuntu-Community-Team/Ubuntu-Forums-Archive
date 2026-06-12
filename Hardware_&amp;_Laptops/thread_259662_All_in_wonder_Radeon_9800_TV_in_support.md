---
title: "All in wonder Radeon 9800 TV in support"
date: 2006-09-17
forum: Hardware &amp; Laptops
---

### Post by d1sturbanc3 on 2006-09-17
Okay I finally got myth tv installed, but I can't locate any driver for the all in wonder.

I know that it is supported by the GATOS, and I managed to apt-get install that package. But where in the /dev is it? I can't seem to find anything.

I tried to run gatos-conf, but it's still on xfree86 .... Should I try compiling the source?

Help? Thanks

---

### Post by d1sturbanc3 on 2006-09-17
okay after reading a bit I see that mythtv doesn't work with the all in wonder card.... but gatos's website says I can still watch tv.

It also says the X now contain the driver for it... but I can't seem to find /dev/video0

---

### Post by d1sturbanc3 on 2006-09-21
bump anyone help me with this?

---

### Post by watson540 on 2006-11-10
Yes, I can. There is no /dev/video and never will be using the GATOS drivers, they use XV and therefore (if you're lucky enough to get a clear picture) you can only use xawtv, avview, and/or possible mplayer/xine. No tvtime or any cool programs work with it. My advice, go buy a hardware based tuner off of ebay for 10 bux based on bt878 or cx878 chipset and save some headache
/me needs to take my own advice

---

