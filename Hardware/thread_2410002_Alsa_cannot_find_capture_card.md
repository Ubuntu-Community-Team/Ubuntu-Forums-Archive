---
title: "Alsa cannot find capture card"
date: 2019-01-09
forum: Hardware
---

### Post by camerondtrain on 2019-01-09
I have a headless machine running Ubuntu server 16.04. I am trying to record audio and video from a Hauppauge ImpactVCB-e PCI Express video capture card. Currently I can record video but not audio. The audio input of the capture card is listed in ```
/proc/asound/cards
``` but it is not listed when I run ```
arecord -l
```. I expect this is an issue with my Alsa configuration, but I don't know how to fix it.

---

### Post by camerondtrain on 2019-05-25
This question has been answered on stack exchange, [https://superuser.com/questions/1393448/alsa-cannot-find-capture-card](https://superuser.com/questions/1393448/alsa-cannot-find-capture-card).

---

