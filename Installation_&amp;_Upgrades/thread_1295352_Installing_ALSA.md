---
title: "Installing ALSA?"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by TheWonkits on 2009-10-19
I have the Hercules Fortissimo II sound card, and the ALSA project says that's supported by their utility...

The problem is, I'm not very Ubuntu-savvy yet..

Can anyone explain how to install ALSA? In semi-english (you don't have to completely dumb it down for me, just mostly)?

---

### Post by Vigh on 2009-10-30
i would love to know myself, and how to configure it to work properly, im getting issues starting the JACK server and getting crackling noises with some of the synths ive got, my guess is

sudo apt-get install alsa

but configuring it im not sure

---

### Post by macogw on 2009-10-31
ALSA is included.  It's got 2 pieces.  One is alsa-kernel, the part that is included in the kernel.  It's the drivers.  The other is alsa-lib, the part that applications use to talk to the part in the kernel.

---

