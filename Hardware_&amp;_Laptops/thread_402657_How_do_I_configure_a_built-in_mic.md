---
title: "How do I configure a built-in mic?"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by wersdaluv on 2007-04-06
I tried KRecord to determine whether or not my mic works, apparently, it does not.

How do I configure a built-in mic?

I have BenQ Joybook R31E laptop running Kubuntu Edgy.

---

### Post by freewill07 on 2007-04-06
Also have the same issue... Help anybody.

---

### Post by wersdaluv on 2007-04-06
Bump.

Help. Anyone?

---

### Post by cakper on 2007-04-16
HI, I have the same problem, my mic in Benq p51e not working, i compiling a new alsa, but this don't helped me

---

### Post by apienk01 on 2007-04-19
I also own Benq P51e and have the same problem. The support for its HDA sound chip, Conexant 5045 - a.k.a CX20549 and CXT5045 (Venice) - has been added to ALSA starting from 1.0.14r2, but still is very preliminary.

---

### Post by jml on 2007-04-19
I use Gnome not KDE, but I have heard of a similar problem.  When you open your sound management application, (Kmix?)  make sure your built in mic is activated.  In Gnome it turns out that the mic input jack is activated by default and the internal mic is deactivated.  Don't know if this also applies to KDE but its worth a try.  Hope it helps.

Joe

---

### Post by apienk01 on 2007-04-29
I found the solution. It seems that the support for the audio chip in Benq P51E (Conexant Venice) has been added to alsa only recently. I compiled the newest alsa drivers from [alsa project website]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2") and voila! - everything works. I can finally use the mic. :)

---

