---
title: "Headphones not working"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by Veinor on 2007-07-06
I have an HP Pavilion dv9000, and whenever I try to plug in a pair of headphones, they don't work. The sound still comes out of the speakers, but none comes from the headphones. I have tried this on a 6.06 live cd, with the same effect. They work fine on a Windows installation.
EDIT: Nevermind; download the latest version of alsa and added ```
options snd-hda-intel model=laptop-hp
``` to /etc/modprobe.d/alsa-base, and all was well after a reboot.

---

