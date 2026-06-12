---
title: "Noise during booting"
date: 2010-06-01
forum: Hardware
---

### Post by ternyk on 2010-06-01
Hi,

I have a problem with sound during booting - when gdm shows its screen it plays a sound from the theme but also it plays a noise for a few seconds. Then after providing credentials and during loading desktop, the same: sound + noise. When the desktop is loaded all works perfectly.
I suppose it comes from my tv tuner card. I have an Abit NF7-S v2 motherboard and two saa7134 based analog tv tuner cards (KNC One DVR).
I don't know how to investigate it to see messages during loading and see what is causing the noise. Any suggestions?

---

### Post by dino99 on 2010-06-01
Startup>Autostart>GNOME Login Sound.

---

### Post by ternyk on 2010-06-01
It won't help. I've found that this problem is already reported: [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/199883](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/199883)

---

