---
title: "nv vs. nvidia problem (resolution and glx issue)"
date: 2008-09-12
forum: Hardware
---

### Post by M.ost on 2008-09-12
Hey all.

This is my first time posting in this forum, but I've been reading it for a week straight trying to look for a solution to my problem.

Just like many other threads I've seen, I am having nvidia issues after updating my kernel.  Currently I'm using a nvidia geforce 7300 GT with the x86 linux 96.43.07 drivers configed from outside of the xserver so the kernel was compiled correctly.  Anyway even after that whole process the only screen resolution that appear are 800x600.  I've done quite a bit of editing with the xorg.conf file adding modelines and refresh rates (basically anything I could find on the threads) with no success and no changes whatsoever.  

However, I have noticed something interesting.  With these drivers installed, the glx rendering and 3d acceleration works, and I can play games and the like in incredibly low resolution.  When i change "nvidia" to "nv" in the xorg file, the resolution gets auto detected correctly to 1440x900, but I lose the ability to use 3d acceleration and thus can't play games.  It feels like I'm one tiny step away and simply need to bridge the gap so to speak.  I need to leave for a bit, so I dont have time to leave a copy of the xorg files.  However, any help or insight into this issue would be greatly appriciated.

---

