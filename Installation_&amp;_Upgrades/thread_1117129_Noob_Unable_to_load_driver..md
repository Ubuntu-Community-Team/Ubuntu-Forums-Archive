---
title: "Noob Unable to load driver."
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by devious_01 on 2009-04-05
Hi there.  I'm trying to install a driver for an NVIDIA Vanta/Vanta LT and don't seem to be able to do it.  Every time I think i have it, then i reboot, there is northing listed in /etc/X11/xorg.conf.... it just says:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Could someone please help me out?

---

### Post by 73ckn797 on 2009-04-05
I have not used that Nvidia card but have you checked System/Administration/Hardware Drivers for any recommended driver?

---

### Post by devious_01 on 2009-04-05
i did as you requested and there is nothing listed there

---

### Post by 73ckn797 on 2009-04-05
Have you enabled "Proprietary drivers for devices (restricted)" in System/Administration/Software Sources?

---

### Post by devious_01 on 2009-04-05
it is checked off under Ubuntu software

---

