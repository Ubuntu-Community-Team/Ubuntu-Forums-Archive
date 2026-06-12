---
title: "TwinView and display brightness"
date: 2006-07-28
forum: Hardware &amp; Laptops
---

### Post by kris42 on 2006-07-28
Hi,

My setup: Kubuntu Dapper, Toshiba Satellite Pro M30, nVidia Geforce FX 5200, Acer AL1912 external monitor.
I managed to get my external monitor working in TwinView mode, but I have one big problem: My laptop's built-in monitor is set to minimum brightness, so the screen is so dim that it's unusable. I can't change the brightness either with the FN-Keys or KLaptop. 
I was wondering if anybody has encountered this problem and knows a solution?

My xorg.conf (obviously irrelevant sections omitted):

```

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

# [Input device sections etc.]

Section "Device"
	Identifier			"NVIDIA Corporation NV34M [GeForce FX Go5200 32M/64M]"
	Driver				"nvidia"
	BusID				"PCI:1:0:0"
	Option "TwinView" 		"True"
	Option "TwinViewOrientation" 	"RightOf"
	Option "UseEdidFreqs" 		"True"
	Option "MetaModes" 		"1280x1024,1280x800"
EndSection

Section "Monitor"
	Identifier	"Default Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go5200 32M/64M]"
	Monitor		"Default Monitor"
	DefaultDepth	16
#	[Modes subsections omitted]
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by kris42 on 2006-07-30
Anyone?

---

### Post by kris42 on 2006-08-02
Ok, I figured out now that the command "sudo toshset bl on" does the trick ... still annoying, but a giant leap forward.

---

### Post by galileon on 2007-04-02
or maybe you could adjust brightness on the external monitor?

---

### Post by maxamillion on 2007-04-02
```
sudo nvidia-settings
```

---

### Post by galileon on 2007-04-02
would that not simply adjust the brightnedd on the card, thus affecting both screens?

---

