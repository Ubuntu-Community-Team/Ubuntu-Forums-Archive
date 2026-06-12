---
title: "Resolution problem"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by LiquidInferno on 2006-10-18
I have a Dell XPS M140 laptop, and ubuntu only has 1 resolution for it (1024x768). Here is an excerpt from my xorg.conf file:

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

I would like to increase my resolution - does anyone have any suggestions?

---

### Post by divague on 2006-10-18
if you're using dapper, this could help you

[http://ubuntuguide.org/wiki/Dapper#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Dapper#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by LiquidInferno on 2006-10-18
you are god - thank you!

---

