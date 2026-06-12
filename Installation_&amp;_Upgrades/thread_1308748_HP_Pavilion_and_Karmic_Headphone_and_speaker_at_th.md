---
title: "HP Pavilion and Karmic: Headphone and speaker at the same time"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by trx64 on 2009-10-31
This problems started in Karmic. Whem I plug my headphone, the sound keep coming from the speaker and from the phone at the same time! How can I solve that?

EDIT: Problem solved. Add the following line at the end of the file /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=hp


And reboot. This will solve the problem.

---

