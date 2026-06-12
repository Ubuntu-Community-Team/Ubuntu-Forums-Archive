---
title: "Laptop Medion 98300 ALSA-problems"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by prinz_valium on 2007-09-27
Hi, i compiled and installed alsa-driver 1.0.15rc2 and alsa-lib 1.0.15rc2 and alsa-utils 1.0.15rc1
I use a 5.1 Dolby-Soundsystem connected to my Laptop (Medion 98300)
now i've written in the "/etc/modprobe.d/alsa-base": options snd-hda-intel model=3stack-6ch-dig

but this is not the best, with this I can't disable the low-quality laptop-speaker... but for real soundfealing i have to...

now my question is:
what is the option i've to write into the alsa-base, works with a medion 98300?

oh, "options snd-hda-intel model=medion" won't give me any sound...

(sorry for the ugly english... will work on it :))

---

