---
title: "LG P1 Express sound"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by Burkey on 2006-07-19
I have an LG P1 Express, Pentium core based laptop.  It has an Intel ICH7 (Hight Def Audio) sound card hooked to an ALC880 in some fashion.

With a default install of Dapper I get sound working fine out of the headset, I can even enable the digital out and see the red led but with nothing plugged in cannot get any sound out of the speakers built into the laptop.

This seems to be a hard problem with all the people I have spoken to so far with this hardware setup.  It really is a shame since the speakers sound so good under windows!

Has anyone got any advice on this?

---

### Post by carlosmolines on 2006-09-14
Sorry for my english but i'm spanish

You added a file /etc/modprobe.d/snd-hda-intel with the line "options snd-hda-intel model=lg"

Visit [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2391](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2391)

---

