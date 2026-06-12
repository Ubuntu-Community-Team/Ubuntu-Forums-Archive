---
title: "How to remove NVIDIA driver"
date: 2019-05-05
forum: Hardware
---

### Post by blupace on 2019-05-05
Hi,
So my machine has a NVIDIA Quadro p400 card. I tried to install the propriety drivers from ppa:graphics-drivers but this just kept freezing my machine.

I took the card out and can boot into Ubuntu just fine with my Intergrated Graphics card, but how can I remove the propriety NVIDIA drivers and get the standard ones back?

Running Ubuntu 19

Regards

---

### Post by pqwoerituytrueiwoq on 2019-05-05
this command will remove anything nviida installed via the package manager (not the .run file you get on the nvidia web site):
[FONT=courier new] sudo apt-get purge nvidia-*[/FONT]

---

