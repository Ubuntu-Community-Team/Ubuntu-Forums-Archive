---
title: "Live CD displaying off centre"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by roncrump on 2006-01-04
Hi,

I was having a play with the Live CD last night -just taking a look, not on the machine I plan to install Ubuntu on (don't have that one yet).

Anyway, when Ubuntu came up, the desktop was shifted to the right - that is, there was a black strip down the left side and some of the right hand side (eg almost all of the trash can icon) was off the screen.

I am guessing that this was a hardware recognition thing, either display or video card, but have no evidence to back this up. Any suggestions as to what it is , and can I fix it.

As I said, I am only looking around at the moment and not on the final target PC (which will be a Toshiba laptop, about 3 years old TE2100, I think), so this is neither urgent nor vital, just a query out of interest.

Regards,
Ron

---

### Post by handy on 2006-01-04
If not a simple monitor adjustment then this is usually caused by the screen refresh rate not being set correctly, in **/etc/X11/xorg.conf**

Have a look here to find out a bit more about this, skip to the **Graphics:**  section if you find the other uninteresting.

[http://ubuntuforums.org/showthread.php?t=88639&page=2](http://ubuntuforums.org/showthread.php?t=88639&page=2)

I wouldn't worry about it with the live cd.  It is nothing serious.

All the best,

handy

---

### Post by roncrump on 2006-01-05
Cheers. I'll take a look.

---

