---
title: "Lines across screen"
date: 2008-05-08
forum: Hardware
---

### Post by LeeU on 2008-05-08
I am running Ubuntu 7.10. Occasionally, I get lines across the screen at different angles. My xorg.conf files seems to be in order (see below for portion of it). I am using a resolution of 1024x768 with a refresh rate of 70.
```

Section "Device"
	Identifier	"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Envision EFT"
	Option		"DPMS"
	HorizSync	30-72
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
	Monitor		"Envision EFT"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

If I switch to another program and then back, the lines disappear. (I also get occasional screen freezes but "seems" to be a Firefox thing.)

---

