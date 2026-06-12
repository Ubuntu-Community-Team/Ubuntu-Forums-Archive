---
title: "Dell Latitude E5410"
date: 2010-11-19
forum: Hardware
---

### Post by ricomoss on 2010-11-19
I've been having a lot of trouble getting linux on my new laptop (Dell Latitude E5410).

After much research I found a post in the Laptop COMPATIBILITY forum stating:
> 
Dell Latitude E6410. Perfect which the following minor caveats:
- had to use "nomodeset" in the boot options before install. And make sure it's in /etc/default/grub GRUB_CMDLINE_LINUX
- while we are in that file: GRUB_GFXMODE=1440x900
- cannot find the microphone, but I'm not even sure there is one with the embedded webcam
- smart card reader doesn't have a driver: "mmc0: Unknown controller version (2). You may experience problems" (but I don't care)

All the rest: bluetooth, wifi, dual screen, etc... worked out of the box.


He is using Kubuntu 10.04 Lucid Lynx.

I was able to get "nomodeset" but didn't know how to access /etc/default/grub to make the other changes.  When I tried to continue with the installation my screen eventually went black and I got the "kernal panic" where my caps lock and scroll lock LEDs keep flashing.

Any suggestions?

---

### Post by filleellif1987 on 2011-01-05
Have you solved this? I recently had the same issue but managed to get things working.

---

