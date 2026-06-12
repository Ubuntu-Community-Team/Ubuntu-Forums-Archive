---
title: "External monitor problem with Thinkpad X61 Tablet Laptop"
date: 2009-02-17
forum: Hardware
---

### Post by jdabgotra on 2009-02-17
Hi, I'm running intrepid, both 32 bit and 64 bit versions, on my Thinkpad X61 tablet laptop. Both of them have this problem -- the laptop monitor brightness is low, and if I adjust it using the deskbar applet nothing happens -- it stays low. Sometimes when I boot up, magically, the monitor brightness is all the way up. Here is my xorg.conf -- i appreciate all your guys' help. 

On the 64 bit, I do not believe I have the intel video driver, which is only available for i386:
[B]

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2704 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection[/B]

I don't post the i386 version of Intrepid I have on this machine, because I have 4gb of memory so am trying to stick with 64 bit. However, does anyone know if there is a solution for the intel video driver?

---

### Post by nnahler on 2009-02-17
From my observation this has nothing to do with your Xorg.conf.

I have a X61 (non-tablet) and had exactly the same problems over the last couple of days. This is due to a kernel update and affects quite a lot of laptops. See here:

[http://ubuntuforums.org/showthread.php?p=6750329#post6750329]("http://ubuntuforums.org/showthread.php?p=6750329#post6750329")

This sorted the problem for me. I went back to the 2.6.27-9 kernel.

---

