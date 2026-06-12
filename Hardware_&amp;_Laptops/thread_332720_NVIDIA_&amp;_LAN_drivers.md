---
title: "NVIDIA &amp; LAN drivers"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by joopajoo on 2007-01-06
My ubuntu version is 6.10 and the default installation.

I downloaded the NVIDIA drivers from their site, and tried install them like the readme says.
The problem is that setup program tells me to try again without XWindow, how am I supposed to start ubuntu without XWindow.
Tried CTRL+CLT+F1 in log in window, but still the same error.

Second problem that I am trying to install LAN drivers, but I get error line:
When i type in ./install.sh
./install.sh: 69: Syntax error: "(" unexpected

The drivers are downloaded from Asus site.

My computer is

Core2Duo 6400
Asus P5B dlx wifi
1gt ram
samsung p120 Sata 300gt

---

### Post by obrouni on 2007-01-07
For my Nvidia GFX card, I just put this add this repository:-

deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable

---

