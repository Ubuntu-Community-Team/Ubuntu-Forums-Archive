---
title: "trying to get SLI working, need help"
date: 2008-11-12
forum: Hardware
---

### Post by filthyphil on 2008-11-12
I installed ubuntu intrepid with 1 7900 GS card in my system. I am trying to add a second 7900 in SLI to it. I found some info here on the forums and added 2 lines to my xorg.conf:

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option	"SLI"	"SFR"
	BusID	"PCI:01:0:0"
EndSection

When I boot with both cards in, I see the splash screen but when X starts my screen goes blank. I'm using the 177.80 nvidia driver.

edit: I removed the nvidia driver, added the lines to xorg.conf, booted with 2 cards, and re-installed the driver, but when I rebooted after that, the same thing happened.

---

