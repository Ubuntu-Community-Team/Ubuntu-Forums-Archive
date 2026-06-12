---
title: "HP Mini 110 and Ubuntu issues... Mi solution?"
date: 2009-09-07
forum: Hardware
---

### Post by brandongu on 2009-09-07
Ever since i installed Ubuntu on my HP Mini 110 netbook, the audio has not worked (except for one random time during boot, but never before or afterward, and i cant imagine what caused it) and neither has the webcam..at least not well. Ive seen and tried so many different so-called fixes, but to no avail. (Alsa recompilaton, settings, etc...) and i was wondering if maybe, since HP's Ubuntu based distro MI im sure is fully compatible with HP minis, would it be possible to take the drivers (or something of the sort) from the Mi distro and implement them in 9.04? sorry if this is an asinine idea, im new(ish) to linux.

I would love to keep ubuntu but the computers basic functions need to work. (although thats mostly an empty threat... i fubarred the OEM XP install when i was repartitioning fo install fedora, which i since replaced with ubuntu, and to replace XP i installed my copy of the WIndows 7 RC build 7100... also has audio probs and if i recall correctly, no webcam.)

---

### Post by aysiu on 2009-09-07
You can try this HP Mini remix. I haven't tested it on the 110 (only 1120nr), but I had similar sound issues on my HP Mini, and maybe it has almost the same hardware as the 110.

It's worth a shot.

[http://www.psychocats.net/hpminiremix](http://www.psychocats.net/hpminiremix)

---

### Post by aysiu on 2009-09-07
You can try this HP Mini remix. I haven't tested it on the 110 (only 1120nr), but I had similar sound issues on my HP Mini, and maybe it has almost the same hardware as the 110.

It's worth a shot.

[http://www.psychocats.net/hpminiremix](http://www.psychocats.net/hpminiremix)

---

### Post by brandongu on 2009-09-08
noob here.. tried sound fix "sudo m-a a-i alsa-source" but it said command unknown for sudo: m-a... am i missing something here?

---

### Post by aysiu on 2009-09-08
> **brandongu said:**
> noob here.. tried sound fix "sudo m-a a-i alsa-source" but it said command unknown for sudo: m-a... am i missing something here? That's a fix for broken sound after a kernel upgrade for those who have already installed the remix. You haven't installed the remix, so that command will do nothing for you.

Get the remix here:
[http://psychocats.net/hpminiremix/download/](http://psychocats.net/hpminiremix/download/)

---

### Post by PhilMize on 2009-09-08
Something odd just happened... In 8.10 and up Nic hasnt been working without a fix (not wireless)...

I just installed 8.04 LTS and it worked out of the box!

Fluke?:popcorn:

---

### Post by brandongu on 2009-09-08
oh... i see what you did there. :P anyway, if it were i386 compatible natively instead of the lpia architecture, i would probably install it, but I'm hesitant otherwise.. I'm guessing there is no simple fix for this issue? :/

and hmmm.. must be a fluke, because with Hardy, i didnt have wireless, ethernet, or sound :O.. i know i needed the broadcom and atheros drivers.. but the sound yet alluded me :/

---

