---
title: "vaio sz stuck at &quot;Running local boot scripts&quot;"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by mahmoodn on 2007-12-17
I can not boot my vaio sz340 in Stamina mode (shared graphic). At boot it stuck at:

"[SIZE="3"]Running local boot scripts (/etc/rc.local)"[/SIZE]

but there is no problem in speed mode (use the graphic card). How can I fix this?

---

### Post by Daelyn on 2007-12-17
Have you downloaded drivers for both GFX cards and made the appropriate xorg.conf switcher to support use of both GFX cards?

---

### Post by mahmoodn on 2007-12-18
I did not download drivers, but as I said it works unders nvidia card so I think it has a default driver for it. 

the problem is with intel 945 shared memory. Does it have driver?

Then how can I change xorg.conf properly? what should I add?

---

### Post by Daelyn on 2007-12-18
It should not hang at loading local bootscripts, it should rather go into failsafe graphics mode.

if you start the ubuntu live CD when you have the intel card activated, does it work then?

You should not bother about the memory, it is auto configured.

---

