---
title: "Forcing xserver to use modeline from xorg.conf"
date: 2009-03-17
forum: Hardware
---

### Post by ntt2007 on 2009-03-17
Hi all,

I have a Motion LE1600 laptop with Intel 915M/GMS/910GML graphic chipset. I recently put Ubuntu 8.10 on it. Initially, everything is fine. However, I ran "apt-get update" and "apt-get upgrade" and has big problem with the updated xserver-xorg-intel :(. The screen is now 80% gray out from the right edge!!!

I modified the "xorg.conf" to set driver "vesa". Then it rans but there's a lot of tearing and offseting. So I manually put in the modeline, Horzsync and Vertrefresh for a standard 1024x768@60 monitor and the "vesa" driver works fine.

I want to comeback to use the accelerated xserver-xorg-intel driver but it doesn't accept the modeline at all. The Xorg.0.log don't even mention anything about this user-input modeline. How can I force it to use the modeline I put in xorg.conf? Or can I degrade my xserver-xorg-intel package?

Thanks.

---

### Post by ntt2007 on 2009-03-18
Anybody ?

---

