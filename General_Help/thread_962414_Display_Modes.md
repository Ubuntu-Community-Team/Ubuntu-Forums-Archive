---
title: "Display Modes"
date: 2008-10-29
forum: General Help
---

### Post by InFeh on 2008-10-29
This problem has been bugging me alot since I upgraded to Intrepid Ibex, though not really an Intrepid issue(I think).

I run a dual-monitor setup. Unfortunately, the second monitor(an ASUS VW192s) only runs on refresh rates between 60-70Hz, and my VGA port is somewhat weird when it comes to that, it always reduces the refresh rate by 0.02Hz. After upgrading, options in nvidia-settings have been reduced to only allow that monitor to run on 60Hz and 75Hz. The end result is that I can only run it on 59.98Hz or 74.98Hz, which are both outside the range of my monitor. I've tried changing xorg.conf to 61-70Hz ranges to compensate and, thus forcing the resulting range to land within 60-70Hz. For some reason, this has no effect when checking the result range in nvidia-settings; it does not change at all, though the new mode for the monitor appears as 1440x900 resolution and "Auto" refresh rate. Before upgrading to Intrepid, I was for some reason able to set the refresh rate to 61Hz, 62Hz, 63Hz all the way up to 70, then jumping to 75Hz(which obviously, the monitor doesn't support, meaning the Auto option would be ineffective), so I had to set it to one of the above-mentioned refresh rates.

Is there some other way I've missed to manually correct this problem so my monitor can be used?

---

### Post by InFeh on 2008-10-30
I'd like to bump this if I may, as it is essentially something which may force me back to 8.04.

---

