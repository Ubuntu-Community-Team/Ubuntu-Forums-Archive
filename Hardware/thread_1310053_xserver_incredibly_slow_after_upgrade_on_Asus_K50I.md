---
title: "xserver incredibly slow after upgrade on Asus K50IJ"
date: 2009-11-01
forum: Hardware
---

### Post by sonnemonster on 2009-11-01
Hello,

i've just upgraded my Asus K50IJ from Kubuntu 9.04 to 9.10 and it is incredibly slow. Using the top command i found out, that Xorg is using 99% of my CPU-Load, even if i'm only moving my mouse around. New windows need a few seconds to appear. I heard, that there are a few troubles with intel-cards, but everything worked fine in Kubuntu 9.04.

In the Xorg.0.log i found

drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1

and so on until card14 and a second time without the Messages from drmOpenByBusid. After that it sais:

(EE) intel(0): [drm] Failed to open DRM device for : No such file or directory
(EE) intel(0): Failed to become DRM master.

Another error is:

(EE) intel(0): Failed to initialize kernel memory manager

I've also got some troubles with MySql, but i think they are not related, so i wont post them here.

Thank you very much in advance...

---

