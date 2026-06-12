---
title: "CS4281 randomly working. Alsa &amp; ESD conflict?"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by isw on 2006-06-09
Ok, weird feature...

Sometimes when I start my laptop (thinkpad 240x) the sound works great.. but sometimes its silent or simply odd and it works by completely random order.

it seems to be some sort of conflict, because at some boots xmms only works with libALSA.so and sometimes only with libesdout.so.

The rest of the system works better when alsa-driver is active, vlc, mplayer, rhytmbox etc.

When using libesdout.so xmms and rhytmbox reports wrong length of mp3 files.
System sound uses ESD though and that works fine.

How do I disable ESD completely, so the default will always be alsa driver? 

thanks

-- isw

---

