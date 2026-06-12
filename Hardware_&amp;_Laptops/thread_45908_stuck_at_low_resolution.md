---
title: "stuck at low resolution"
date: 2005-07-02
forum: Hardware &amp; Laptops
---

### Post by numerodix on 2005-07-02
I've been running Windows on my box for ages and I thought I would give ubuntu a shot today. I was planning to use the same screen resolution that I do in Windows, which is 1280x1024. but I've run into some problems with that. I edited /etc/X11/xorg.conf to include 1280x1024 and make it the default resolution but I was still getting 1024x768. I then removed all the others to force Xorg to use the one I wanted but then I got 1280x768 instead for some reason. I also tried setting the depth to 16 but that didn't help either. So now I'm stuck at either 1024x768 or 1280x1024.

I know that both the monitor and video card are well capable of doing this, since I've done it for ages in Windows. I looked in /var/log/Xorg.0.log but I don't see any errors being reported.

lshw doesn't do a good job of identifying my card:
```
           *-display UNCLAIMED
                physical id: 0
                bus info: pci@02:00.0
                version: a3
                size: 128MB
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: irq=11
```

But Xorg tells me this:
```
(**) |   |-->Device "NVIDIA Corporation NV17 [GeForce4 MX 440]"
(--) PCI:*(2:0:0) nVidia Corporation NV17 [GeForce4 MX 440] rev 163, Mem @ 0xe3000000/24, 0xe8000000/27, 0xe7800000/19, BIOS @ 0xe77e0000/17
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,

```

Any ideas?

---

### Post by frodon on 2005-07-02
post here your xorg.conf file, and i think your problem will be solve. Probably HorizSync and VertRefresh parameter are too low. Try to increase the upper limit of these parameter ... but with your xorg.conf it will be easier to help you.

```
section "Monitor"
	Identifier	"Écran générique"
	Option		"DPMS"
	HorizSync	28-149
	VertRefresh	43-172
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Écran générique"
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
EndSection
```

---

### Post by numerodix on 2005-07-03
Yeah, it turns out my vsync/hsync was just set to default values and I have the correct settings printed on my monitor, that took care of it. :)

---

