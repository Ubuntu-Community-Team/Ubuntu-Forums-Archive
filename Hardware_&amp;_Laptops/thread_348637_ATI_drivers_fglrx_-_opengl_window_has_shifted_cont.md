---
title: "ATI drivers fglrx - opengl window has shifted content"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by virgee on 2007-01-29
Hello,
hope some of you had experinced, better to say resloved, following issue with OpenGL and ATI Radeon 9600 Mobile.

I have recent (8.33.6) fglrx drivers on my 6.06 box and when I run any opengl app (foobilliard, my own apps in java with JOGL, ...) I get opengl rendered parts of app window shifted to the left, behind window border (and thus they can not be seen).

I encoutered this problem with older drivers too (but it used to be OK in the past).

Thanks for any help

---

### Post by mizar001 on 2007-01-29
To state if it's a problem of opengl you should try other opengl apps, instead of JOGL coded apps. Maybe your JOGL library does not fit for your card.

Some screensavers have opengl capabilites. Do those apps have this problem ?

In some case, before installing driver, be sure to uninstall the preceding one, or do a reconfiguration of Xorg.

---

### Post by virgee on 2007-01-29
I tried with regular OpenGL apps (foobilliard), but my fault - I did not say that clearly.

Anyway, I reverted to few months old xorg.conf without dual head configuration, and it works fine now. Thanks for showing the way to me, the n00b ;)

---

