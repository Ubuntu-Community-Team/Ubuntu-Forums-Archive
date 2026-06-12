---
title: "Ubuntu 14.04 on Dell Inspiron 14z running hot when idle"
date: 2014-08-10
forum: Hardware
---

### Post by Buuntu on 2014-08-10
My Dell Inspiron 14z-5423 has been running really hot in Xubuntu 14.04.  It hasn't been shutting off or anything yet but my Windows 7 partition runs **significantly** cooler.  I tried booting from a live CD to see if it was some software that was causing the issue but I had the same problem.  CPU and GPU usage are very low which I checked with top and intel_gpu_top so I'm not sure what's causing the issue.

Although there is a Dell Inspiron 14z-5423 that has a dedicated AMD card mine only has the integrated Intel 4000 graphics card (I ordered the i14z-5000sLV but the bottom of the laptop says 14z-5423 which is confusing).  I also tried installing indicator-cpufreq and setting the CPU mode to "Powersave" but that didn't seem to make a significant difference.

I realize that the temperature might still be within the okay range even though the back middle part of that laptop feels really hot to the touch.  In my opinion way hotter than it should and much hotter than it does in Windows.  I'm not even sure it's the CPU, lm-sensors usually shows it to be between 55-60 C when idle which doesn't seem too bad (I've seen it up to 75 C when the CPU is at 100% for a while).

Anything else I could try?

---

