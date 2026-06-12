---
title: "Problem with Intel Drivers"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by thomasz64 on 2009-05-18
Hi, I upgraded system from 8.10 to 9.04 on my notebook TravelMate 2492NWLMi. I used "Reverting the Jaunty Xorg intel driver to 2.4" of the wikiubuntu site, because my video players crashed after starting. This problem was removed.
But second problem is yet:
    - When I start video on youtube, then Mozilla(and other explorer) crash. 
    - Scrolling (in Mozilla, Evince, ..etc.) is very slow and CPU 100%.
    - all motions windows are very slow and CPU 100%.

I don't know, what to do.
I uninstalled compiz,but nothing change.

lspci -nn|grep VGA:
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

uname -r:
2.6.28-11-generic

Thanks for helping.

---

