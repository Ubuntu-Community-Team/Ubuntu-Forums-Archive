---
title: "No good sound"
date: 2008-04-28
forum: Hardware
---

### Post by duckydude on 2008-04-28
Hi, I have a Toshiba Satellite A135-S4427, which has a Realtek ALC861-VD chip and an HDA Intel card, and using ALSA, I couldn't get sound, but if I switched to OSS, I got sound, but only through the speakers, and not the headphone jack, which I would've preferred in some situations, and I was wondering if I could get ALSA to work, OK? ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by jbernardo on 2008-04-28
Check [this bug]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382"), I have exactly the same chip, look for my entries in the bug report. Basically you need to compile the alsa driver, and set options in /etc/modprobe.d/alsa

---

### Post by duckydude on 2008-04-28
Thanks, those solutions worked, and same with headphones. :)

---

