---
title: "alsa failed"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by qhimq on 2008-02-13
hi

I was messing with my xorg.conf file and somehow i'm afraid ubuntu reset some things.  For instance it reset my boot parameters back to what they were when I installed, and now there are no sound cards visible to alsa.

I tried: asoundconf list
and it prints no sound cards.

I tried: alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

I had a copy of the good xorg.conf and I used it however it didn't change the fact that alsa doesn't work.

help:confused:

---

### Post by TheLions on 2008-02-14
recompiling alsa should work...

---

