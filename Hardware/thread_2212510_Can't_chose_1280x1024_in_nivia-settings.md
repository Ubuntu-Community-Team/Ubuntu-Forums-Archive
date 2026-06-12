---
title: "Can't chose 1280x1024 in nivia-settings"
date: 2014-03-21
forum: Hardware
---

### Post by Azyx on 2014-03-21
Hey.
I have an 02:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520] (rev a1) on Ubuntu 12.04

As a primary display I have an Fujusi Siemens FUS L24W 24" 1920x1200 screen and a secondary a Fujitsu Siemens CMT7010 1280x1024. The problem is that I don't can chose 1280x1024, only 1152x864 on the secondary display in **[COLOR=#008000]NVIDIA X server Settings [/COLOR]**:(  I have the proprietary drivers, nvidia-settings 331.20-0ubuntu0.01 and nvidia-common 1:0.2.44.2

Cheers.

PS. Ubuntu don't seems to have Xorg.conf any more.

---

### Post by Azyx on 2014-03-26
Seems to have being a problem with the vga-cable (missed 2 pins instead of 1 pin). Anyway, it works now with 1280 x 1024 and the native resolution.

---

