---
title: "Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter"
date: 2010-12-16
forum: Hardware
---

### Post by narcisgarcia on 2010-12-16
I'm trying to configure graphics with this dual display adapter in a "Fujitsu-Siemens Esprimo mobile v5535" laptop with Ubuntu GNU/Linux 10.10 (Maverick Meerkat).
The two problems I have now are: the lack of 2D acceleration and the moved+cropped image on external television. I'm still using the default vesa mode and cannot make difference between displays with gnome-display-properties.

I've tried to use the "sisimedia" driver (version 0.9-1) with the package [provided by Dennis Schulmeister]("http://ncc-1701a.homelinux.net/~linux-sis/"), but fails to load with this error:
> /usr/lib/xorg/modules/drivers/sisimedia_drv.so: undefined symbol: resVgaIoShared 

I've read in other forums that somebody solved the acceleration issue with Ubuntu 10.04 (Lucid Lynx) installing the version 0.9.1-2 of the sisimedia driver, but I neither find any 0.9.1-2 package nor the Mandriva source/repository to make a new .deb package.

---

### Post by Zli Zeka on 2011-07-02
Anyone?

Update?

---

