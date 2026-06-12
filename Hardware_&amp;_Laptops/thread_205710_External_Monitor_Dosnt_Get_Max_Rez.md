---
title: "External Monitor Dosnt Get Max Rez"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by noob_Lance on 2006-06-28
Hey... i have tired getting my monitor (external) to get its max rez.. 1280x1024 but Dapper dosnt want to.. it goes back to 640x480 and thats all i can get..

can anyone help me please... :)

~Lance

---

### Post by soapyfish on 2006-06-29
I have the same problem Fresh install of 6.06 + updates +nvidia-glx drivers  I have  included a same of my xorg.conf 

Section "Device"
	Identifier	"NVIDIA Corporation NV20 [GeForce3 Ti 200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

ection "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV20 [GeForce3 Ti 200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection

I have 3D graphics  or at least I have the nvidia logon displayed at logon time so I think its all ok except for the max resolution being 1024x768  NOT   1280x1024  any help would be great ! :-)

---

### Post by noob_Lance on 2006-06-29
forgot to mention... i have an intel chip lol.

---

