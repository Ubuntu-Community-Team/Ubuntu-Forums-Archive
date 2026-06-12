---
title: "and again - sound problem"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by Keymone on 2007-08-06
i can hear sound only through OSS
ALSA does not want to produce anything

updated to latest drivers --with-cards=hda-intel (or smth like that don't remember), made it model=6stack-dig

all i got - huge number of controls in alsamixer and nothing except noise..

any ideas how to completely delete sound system and install it from scratch? i can't even remember all things i've tried to make sound working.

my mb is ASUS P5LD2

thanx

---

### Post by Keymone on 2007-08-06
P.S. isn't it a bit confusing to have 10 diferent sound systems like ALSA, OSS, ESD etc? why not to stick to best one and make it "just work"? nobody will will switch to ubuntu if they have to compile drivers / configure modules... when i say nobody it means "none of regular windows users" :)

---

### Post by nickdngr on 2007-08-06
i don't know if this is good advice, but i've been having sound problems as well. basically, the sound will just die and in rhythmbox it will jump seconds. like it will go 1, 4, 6, 15, 32... in a span of 2 or 3 seconds. I discovered that  by going to system, administration, system monitor, processes that there was a process called ESD (enlightened sound daemon) running. i killed the process and it seems to solve my audio problems. maybe that may help....

---

