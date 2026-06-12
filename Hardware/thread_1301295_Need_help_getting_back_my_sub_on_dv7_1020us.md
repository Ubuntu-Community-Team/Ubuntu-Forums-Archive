---
title: "Need help getting back my sub on dv7 1020us"
date: 2009-10-25
forum: Hardware
---

### Post by rolandixor on 2009-10-25
All the guides I've followed come up empty. I really have had it. I can't wait for Karmic, but I need a new hard drive before I upgrade. So can someone help me get it working on Jaunty before I get the second hard drive?

---

### Post by Daniel Libonati on 2011-06-14
Try adding the following line to your /etc/modprobe.d/alsa-base.conf :

options snd-hda-intel model=ref

That was the only thing that worked for me.

---

