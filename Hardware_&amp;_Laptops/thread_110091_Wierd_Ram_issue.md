---
title: "Wierd Ram issue"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by Mikeynewbie on 2005-12-30
Hey all I recently upgraded my RAM to 1 gig.  Everything seems fine but on occasion if I am ripping a cd using banshee things slow down and then the system monitor says i am using all 1 gig of Ram I check processes that are running and it shows no where near 1 gig of running processes.

Anyone have any idea what may be happening here

I am running Breezy 386 on a compaq presario with amd 3000+xpm processor 1 gig ram as stated before.  with dual boot windows xp pro (ewwww, but gotta keep until the thesis is done).

---

### Post by roachk71 on 2005-12-31
[LEFT]You may want to install the 686 kernel.

The 386 kernel really only handles up to 900MB of RAM, and the 686 kernel handles 900MB+ more efficiently. The process scheduling is also better.

Try opening Synaptic and looking for linux-686 (or linux-image-686).

This kernel has eliminated quite a few problems on my notebook as well (HP Pavilion xt125.)

[/LEFT]

---

