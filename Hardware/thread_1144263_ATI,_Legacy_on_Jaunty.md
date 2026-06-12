---
title: "ATI, Legacy on Jaunty"
date: 2009-04-30
forum: Hardware
---

### Post by And1945 on 2009-04-30
Greetings,

My dad asked me to tune up his 8.04 installation, and I went a head. After experiencing some graphics problems upon "login", I found out via this forum, that there seems to have been some movement in the ATI legacy department... [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.11&lang=English")

Anyway. His 9700 mobility is surely one of them, and the xserver is stuck on fglrx or mesa-glx, im not really sure. I tried messeing around the recovery->root->aptitude and went nowhere. The only thing I can get a hold of, is the recovery menu.

His grep glx: libg11-mesa-glx, libglitz-glz1, rss-glx... The usual stuff.

Now the question is, how do I fix this with no apt-get available? At least, not to my knowledge.

---

### Post by And1945 on 2009-04-30
Nevermind.

These packages fixed it, after a init 6.

xserver-xorg-dev x11proto-xf86dri-dev x11proto-dri2-dev libxdamage-dev libxxf86vm-dev libdrm2-dev x11proto-gl-dev

From: [http://wiki.x.org/wiki/radeon](http://wiki.x.org/wiki/radeon)

---

