---
title: "nvidia geforce mx 200 locks up lucid"
date: 2010-06-13
forum: Hardware
---

### Post by Vermind on 2010-06-13
Hi,
I installed Lucid on an old machine with an nVidia GeForce MX 200 card. On startup, I got X running on vesa or nv. Jockey prompted me to install nvidia proprietary drivers (nvidia-96), which had worked on 8.04 before the lucid install. After installing and reboot, I get a black screen when X should start. After much trial and error, I have found that vesa and nv work, but nouveau doesn't find the device (drmOpen fails) and nvidia just locks up with no messages. It leaves the display on, keyboard is unresponsive, AltGr-PrintScreen-K does nothing, trying to switch to VT and ctrl-alt-del does nothing.

The nVidia GeForce MX 200 is the NV11DDR chip according to lspci. According to nVidia's website, the nvidia-96 is the correct driver. I tried also nomodeset and removing quiet and splash from the kernel cmd line.

Any ideas?

---

### Post by quixote on 2010-06-15
Sounds like the proprietary driver has left some oddness behind.  Have you tried uninstalling it with a purge option and reinstalling nouveau?  Nouveau has been working like a charm for my nvidia card (Quadro NVS 135M).

---

