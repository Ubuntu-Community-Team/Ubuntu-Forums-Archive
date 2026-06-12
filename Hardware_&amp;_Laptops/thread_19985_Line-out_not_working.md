---
title: "Line-out not working"
date: 2005-03-14
forum: Hardware &amp; Laptops
---

### Post by Jezze on 2005-03-14
Im using a Acer 4001WLMi Laptop and I would like to be able to output sound from my line-out port but as soon as I insert a cable the sound disappears from the internal speakers (as it should) but no sound is sent through line-out... what should I do in order to activate line-out?

---

### Post by stenbock on 2005-03-15
I hope that you have tried alsamixer. And enabled the sound output/level. My lineout is by default muted.

---

### Post by Jezze on 2005-03-16
That would have been very embarrasing... im gonna check it once i get home...

(jag är också stenbock :))

---

### Post by enda on 2008-02-17
Add the following line in /etc/modprobe.d/alsa-base:

options snd-hda-intel model=acer

Note: You can specify one of the following model : acer, toshiba, 3stack or auto Note 2: For MSI PR200, use model=targa-dig

Mt case (toshiba A135 choose "3stack")

---

