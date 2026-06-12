---
title: "How to install/configure an ATI Rage 128 AGP?"
date: 2010-12-16
forum: Hardware
---

### Post by claus on 2010-12-16
Hi,

a while ago I purchased a used PC with the above graphics card built-in, but I'm afraid to install the xorg driver. With my old PC, I always ran into problems when trying to install the proprietary Nvidia driver (read: no x-server). Is there a safe way to install & configure the driver for this card? What packages would I have to install via Synaptic?

I found a thread with the following values for xorg.conf:

Section "Device"
Identifier "Configured Video Device"
Boardname "ATI Rage 128" {Change this to your card name}
Busid "PCI:1:5:0" {This was detected before. Don't change yours}
Driver "r128"
Screen 0
Vendorname "ATI"
Option "MergedFB" "off"
EndSection

Would those values be ok?

TIA,

Claus

---

