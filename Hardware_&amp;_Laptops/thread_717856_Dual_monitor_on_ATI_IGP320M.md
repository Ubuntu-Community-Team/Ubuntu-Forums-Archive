---
title: "Dual monitor on ATI IGP320M"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by Knightmayre on 2008-03-07
Hey all,

I am a Linux n00b and I cannot for the life of me get my external monitor to work.

I am running KDE4 and every time I modify xorg.conf I break it and have to use my backup.

My graphics card on this laptop is an ATI IGP320M.

When I go into screen size & rotation, the APPLY button is greyed out.

Please, can someone help me reconfigure my xorg.conf?
I have been trying for 4 days to get this working, and I really don't want to go back to  Vista LOL

Thanks.

---

### Post by tormod on 2008-03-07
Unfortunately, "screen size & rotation" is broken for xrandr in 7.10.

From the Ubuntu 7.10 release notes:

Dual-head (multi-screen) setups
  *   The ati driver has dropped MergedFB / Xinerama support in favour of xrandr 1.2 support, and old multi-head xorg.conf setups will break. To set up dual-head see the guides at [WWW] [http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html) or [WWW] [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

---

