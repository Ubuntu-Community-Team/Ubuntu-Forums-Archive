---
title: "LifeView DVB-T DUO problem"
date: 2005-11-22
forum: General Help
---

### Post by rklauco on 2005-11-22
I have a problem with this card.
I re-compiled the v4l for better support and now the TV tuner on the analogue TV works great (better than in windows).
The problem is, that with the new v4l and saa7134 module the card will no longer create a /dev/radio0 device and I can't use an FM tuner.
It did create a /dev/radio0 before, anyhow it did not work.
Any advices/experiences with this peace of HW?

---

### Post by rklauco on 2005-12-18
For those interested...
I found on different forum, that I can use /dev/video0 as a radio device.
It worked for one time, but since than I am no longer able to find a working radio frequency.

---

