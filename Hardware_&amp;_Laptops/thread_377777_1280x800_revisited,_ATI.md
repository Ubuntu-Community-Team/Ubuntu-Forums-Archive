---
title: "1280x800 revisited, ATI"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by one_ro on 2007-03-06
Hi all,

Since there seems to be a "solving" mood for resolutions lately ;) I thought I might give it a shot.
The previous thread about this resolution is about a different video card, mine is ATI.
The proprietary driver is installed and the "fglrx" driver is chosen in xorg.conf
It works like magic with the default resolution of 1680x1050 but I find this resolution a bit too large for my laptop's 15.4" monitor.

I found the proper modeline for the 1280x800 resolution with:
```
gtf 1280 800 60 -x
```This modeline is added in xorg.conf and the link created in SubSection Display (the name of the link is exactly the same with the name of the modeline). Only... the stupid resolution absolutely does not appear in System Settings.

Could anybody point me to a direction, please?
Thanks,
Adrian

---

### Post by namregzepol on 2007-03-12
same problem here with an ATI X1600. ¿no solution?

---

### Post by one_ro on 2007-03-12
Unfortunately nothing yet.
I'm going to keep digging, if I find something I'll let you know.
Cheers,
Adrian

---

