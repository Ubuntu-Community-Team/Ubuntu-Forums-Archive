---
title: "Problem with intel gma 3600 drivers"
date: 2013-07-11
forum: Hardware
---

### Post by anarhisthristov on 2013-07-11
i can't activate the driver for my video card.  "Cedar Trail drm driver in DKMS format" unsuccessful installation of this driver. How to fix it ?

---

### Post by dino99 on 2013-07-11
be sure that : dkms, built-essential and the kernel headers (2) are installed ; then reinstall xserver-xorg-video-intel
(you can install & use synaptic for ease)

sudo apt-get install synaptic
sudo synaptic

---

