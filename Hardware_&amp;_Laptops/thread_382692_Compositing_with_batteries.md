---
title: "Compositing with batteries?"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by hizaguchi on 2007-03-12
I'm wondering what everybody else's battery life is like using compositing window managers, and more importantly, if there is a compositor that is easier on the power consumption than the others.

I get 4+ hours of battery life with just Metacity on the plain Xorg server, with no compositing (using the fglrx driver).  If I use XGL and Beryl, the power manager still says I have 4 hours of battery left at full charge, but it actually drains significantly faster and I end up getting around 2.5-3 hours of life before I need to find a plug.  Obviously this is because of the video card and processor working overtime... so much so that my laptop runs considerably warmer and needs to crank up the fan more often and longer, which adds a secondary problem of noise.

Is there a good way to optimize my battery usage, other than just getting rid of my sexy shadows and transparencies?  Has anybody tried XFCE's built-in composite manager that could compare the battery usage to XGL and Beryl?

---

### Post by mthakur2006 on 2007-07-14
xg/aiglx and/or compositing in general takes up more cpu cycles which means running compositing window manager on windows drains 'em faster.

---

