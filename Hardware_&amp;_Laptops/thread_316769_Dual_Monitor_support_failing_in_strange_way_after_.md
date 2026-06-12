---
title: "Dual Monitor support failing in strange way after upgrade to 6.10"
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by wjbaird on 2006-12-11
Hi all,

I have a Dell D410 latop with an Intel I915 graphics chipset.  I just upgraded from 6.06LTS to 6.10 (I used the upgrade-manager -c mechanism).  I had Xinerama working perfectly with 6.06, but it is now broken in a strange way. 

The external monitor is being activated, and I can see things on it, but for some reason all windows open on the internal monitor, and I can't completely drag them onto the external monitor - it always leaves maybe 50-100 pixels on the laptop screen.

Equally strange, I run a few windows apps using cross-over office, and if I try to resize any of the windows apps to be larger than 1024x768 (the internal montior's resolution) the area outside of 1024x768 doesn't refresh at all.  I don't know if this is related or not.

I verified my xorg.conf, and the only thing that the upgrade process changed was to remove "GLCore" from the list of extensions to load.  I tried adding it back in, and it didn't help at all.

Any advice would be welcome...

---

### Post by wjbaird on 2006-12-13
I've looked into it a bit more, and determined that it *is* an X configuration issue - I've found that xdpyinfo is returning a resolution of 1024x768, even though my actual resolution is 2624x1200 (1024x768 beside 1600x1200).

I've posted a separate question in the appropriate section.

---

