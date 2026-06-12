---
title: "HP Laptop External Monitor"
date: 2006-09-15
forum: Hardware &amp; Laptops
---

### Post by Tonren on 2006-09-15
Hey guys, I'm trying to get the external monitor jack on my HP Compaq Presario v2565US working.  It's a mid-range widescreen laptop... I installed the ATI proprietary drivers - this is my fglrxinfo output:

```
04:32 PM mcantor@zanpakuto ~: fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

When I hit Fn + F4, which is the "external monitor" hotkey, nothing happens.  Absolutely nothing.  I'd really like to get this working WITHOUT changing my xorg.conf to pretend I have two monitors, because I'm not ALWAYS attached to a projector, just when I'm in class!

Can anyone help...?  Thanks!

---

### Post by RafRaf on 2006-09-16
Hi,

I am also looking for the same solution as you are. The best would be working plug-and-play but I have gone through ubuntu guides without any results.

I think you can try the ATI control in the Applications-Accessories folder and set it up to use 2 screens. I tried this but I could not get films to display correctly on my external LCD (which was my goal).

Another way would be to use the command line utility. write aticonfig --help in a terminal.

Let me know how it goes.

cheers!

---

