---
title: "Nvidia GeForce2 Integrated GPU (Asus A7N266-E)"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by gsanse on 2005-09-08
I don't know if anyone else is having this problem, but Xorg was very unstable in my machine after I installed nvidia-glx drivers. I have a Asus A7N266-E mobo with a GeForce2 Integrated GPU. Reading out the nvidia readme file at /usr/share/doc/nvidia-glx I found out that it could be related to AGP problems. Doing the corrections suggested there I was able to fix my problem and xorg is very stable. My xorg.conf now looks like this:

Section "Device"
	Identifier	"NVIDIA Corporation NVCrush11 [GeForce2 MX Integrated Graphics]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option 		"NvAGP" "1"
	Option		"NoLogo"

EndSection

Hope it helps.

gsanse

---

