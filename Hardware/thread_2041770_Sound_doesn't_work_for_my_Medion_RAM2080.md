---
title: "Sound doesn't work for my Medion RAM2080"
date: 2012-08-13
forum: Hardware
---

### Post by Bro Bumble on 2012-08-13
Hi, I recently got this laptop, and have installed Ubuntu 12.04 onto it (previously had Vista).  But the sound doesn't seem to be working on it (I think it's because of the proprietary Nvidia drivers), I've tried googling my problem, but none of the links I found were of any use.  I've also tried using live CDs of various distros (puppy, mint, mageia etc) and the sound doesn't work on any of them.  My chipset is SigmaTel STAC9200 if that helps.

---

### Post by gordintoronto on 2012-08-13
Is this with built-in speakers? Have you tried earphones?

Have you run System Settings, Sound? What devices show up?

Does the laptop have HDMI out?

---

### Post by Bro Bumble on 2012-08-13
> **gordintoronto said:**
> Is this with built-in speakers? Have you tried earphones?

Have you run System Settings, Sound? What devices show up?

Does the laptop have HDMI out?

 Thanks for the reply. After doing a few more (in depth) searches (focusing on the chipset sigmatel STAC 9200) I found that all I had to do was edit the alsa config with the line  at the end "options snd-hda-intel model=gateway-m4". It's working great now.

---

