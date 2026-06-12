---
title: "Very low volume on eeepc 901"
date: 2008-11-01
forum: Hardware
---

### Post by MrNatewood on 2008-11-01
I have installed ubuntu 8.10 on my eeepc 901, sound card intel hda.
Sound is very very weak across all application and system sound. I have checked the PCM volume and it is set to max.
I also tried adding the line "options snd-hda-intel model=3stack" to alsa-base but that didn't help.

How can I fix this?

---

### Post by seeebek on 2008-11-01
Hi MrNatewood,
Everything you have to do is to right click on the sound icon next to the time. Then chose "Open volume control" and chose from the list: HDA Intel (Alsa mixer). Put beside PCM also Lineout to maximum. Then you should have the normal eeepc sound level.
Hope I could help.
best regards,
seeebek

---

### Post by Lingonet on 2009-04-18
Thank you! This helped alot!

---

