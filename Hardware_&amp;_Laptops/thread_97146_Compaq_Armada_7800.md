---
title: "Compaq Armada 7800"
date: 2005-11-30
forum: Hardware &amp; Laptops
---

### Post by waltervalderrama on 2005-11-30
Hello, i have a problem running ubuntu on my Armada 7800 Pentium 2. I cannont switch to 1024 x 768. I tried several times to change the X configuration, run dpkg-reconfigure xserver-xorg, and things didn't change. I have a S3 video card.

Section "Device"
	Identifier	"S3 Inc. ViRGE/MX"
	Driver		"s3virge"
	BusID		"PCI:1:0:0"
	VideoRam	4000
EndSection

Please, need help, becaus i want to work with linux. I already have ubuntu configured on my desktop, but i want to use my laptop now.

---

### Post by teaker1s on 2005-11-30
did you specify correct horzontal sync and refresh etc for lcd

---

### Post by waltervalderrama on 2005-11-30
Nop, i dodn't know. Where i can check those values. I never had to do that

---

### Post by teaker1s on 2005-11-30
you may find them either in you computer documentation or search your model lcd specs in google! someone may be able to tell you more about lcd settings as I only have CRT

---

