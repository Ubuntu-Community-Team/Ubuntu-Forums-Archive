---
title: "[solved]"
date: 2009-04-18
forum: Hardware
---

### Post by synergy_ek on 2009-04-18
Spended many hours making sound works on HP Pavilion tx2650er with Ubuntu 9.04 Jaunty beta (ATI HDA S)
But just one line in /etc/modprobe.d/alsa-base.conf make it works:
options snd-hda-intel model=acer

model=toshiba, model=3stack, model=hp doesn't works for me

---

