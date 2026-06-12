---
title: "Ubuntu 10.10 Sound issue / no headphone sound / Asus M5810"
date: 2011-01-14
forum: Hardware
---

### Post by lvanderb on 2011-01-14
After a recent update, I found that I have no sound in my headphones.

My system is an Acer Aspire M5810.

Here is a link to my alsa-info:
[http://www.alsa-project.org/db/?f=4d17d4fed808870b4ea82a239e4fafca1d90ca32](http://www.alsa-project.org/db/?f=4d17d4fed808870b4ea82a239e4fafca1d90ca32)

Please let me know if there is any other information that is required.

Thanks so much!
Linda

---

### Post by lvanderb on 2011-01-18
After a lot of research, I found that changing my sound preferences to Analog Speakers probably did the trick.
Headphones still have no volume bar, but as long as Master, Headphones and Speaker are unmuted, I get sound in my headphones.
I also edited /etc/modprobe.d/alsa-base.conf to add the following line:
options snd-hda-intel model=m5810 position_fix=0

Linda

---

### Post by lvanderb on 2011-01-18
Duplicate - removed

---

### Post by lvanderb on 2011-01-18
Duplicate - removed

---

