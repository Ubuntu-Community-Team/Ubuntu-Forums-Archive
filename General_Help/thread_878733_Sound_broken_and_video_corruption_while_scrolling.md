---
title: "Sound broken and video corruption while scrolling"
date: 2008-08-03
forum: General Help
---

### Post by John_5 on 2008-08-03
Hey all, I recently got a new laptop, a HP Compaq Presario CQ50.
-AMD Turion 2ghz dual core
-2gb of RAM
-NVidia 8200 512mb vram

Ubuntu installed flawlessly(Except for a corrupt disk I was using). After I installed it I installed the nvidia drivers via Envy.

Heres the problem though.. Sound is not working at all! All I hear is a faint static sound when a sound is meant to be playing. 

Also, while scrolling up/down in firefox and other applications with desktop effects enabled corrupt graphics appear.

Any help is appreciated!

Rock on!! :guitar:

---

### Post by John_5 on 2008-08-04
Bump, please halp :(

---

### Post by John_5 on 2008-08-04
Another bump, would really appreciate a reply :(

---

### Post by bholliday72 on 2008-08-04
System - Accessories - Sound

From here I always change autodetect to my sound card (built in Realtek chipset on Gigabyte GA-EX38-DS4)

Try messing with this, try using your soundcard (if available) , ALSA, OSS, and pulseaudio .  If you have already tried this, sorry.  I have no further suggestions.  Happy bunting!

Also, does your sound work properly in Windows?

Are your speakers hooked up properly?

---

### Post by John_5 on 2008-08-04
> **bholliday72 said:**
> System - Accessories - Sound

From here I always change autodetect to my sound card (built in Realtek chipset on Gigabyte GA-EX38-DS4)

Try messing with this, try using your soundcard (if available) , ALSA, OSS, and pulseaudio .  If you have already tried this, sorry.  I have no further suggestions.  Happy bunting!

Also, does your sound work properly in Windows?

Are your speakers hooked up properly? 

my sound works properly in windows and I've tried messing around with sound options.

Thanks for the help

---

### Post by iucoen on 2008-08-05
> **John_5 said:**
> Hey all, I recently got a new laptop, a HP Compaq Presario CQ50.
-AMD Turion 2ghz dual core
-2gb of RAM
-NVidia 8200 512mb vram

Ubuntu installed flawlessly(Except for a corrupt disk I was using). After I installed it I installed the nvidia drivers via Envy.

Heres the problem though.. Sound is not working at all! All I hear is a faint static sound when a sound is meant to be playing. 

Also, while scrolling up/down in firefox and other applications with desktop effects enabled corrupt graphics appear.

Any help is appreciated!

Rock on!! :guitar:


To fix the scrolling problem, go to preferences -> appearance, and change desktop effects to None. 

Sound is just hopeless. Currently, the HDA driver is broken for all nforce7/Geforce8 chipsets. I have a Geforce8300 desktop, also with broken sound.

---

### Post by Ripfox on 2008-08-11
Compaq CQ50 has very scratchy audio for me...looking for a fix but the device is reported as "unknown" I know it's an Nvidia chipset.

---

