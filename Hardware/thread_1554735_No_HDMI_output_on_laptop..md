---
title: "No HDMI output on laptop."
date: 2010-08-17
forum: Hardware
---

### Post by monster_eater123 on 2010-08-17
I have a Gateway NV53 with a Radeon HD 3200M running Lucid 64-bit. I cannot seem for the life of me to get my HDMI running correctly. It worked fine for about a day then randomly quit all together. Now my TV will say that I have to check the device's power or cable connection. Once i turn off the Power Play setting I can get video but no audio, (even by selecting the device under sound preferences). When I edit my xorg.conf with these two lines under "Devices":

Option "Audio" "true"
Option "HDMI" "all"

I get audio and video but my HDMI is forced on all the time. It mirrors my laptop monitor with no option to switch monitors on or off, (even with my function key setting). I have tried everything I can think of myself. I have even downloaded the proprietary driver straight from the ATI website. Any ideas?

---

### Post by user328 on 2010-08-17
Never mind, can't delete.

---

### Post by monster_eater123 on 2010-08-18
I checked alsamixer and my HDMI sound isn't muted. Idunno what it cold be. HDMI connects fine to my monitor with no sound output.

---

