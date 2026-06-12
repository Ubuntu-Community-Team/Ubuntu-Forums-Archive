---
title: "Can't use compiz or any effects"
date: 2008-09-10
forum: General Help
---

### Post by rocknzen on 2008-09-10
Last night the motherboard in my desktop went bad. So I had to set up my laptop which is an HP dv6110 with nvidia Go 6150 vid card. I wanted to use my 22" Samsung monitor in a twin monitor configuration (actually I don't care about using 2 monitors I just need the larger monitor for my work)
In any case I followed a how to guide to make it work ([http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)) and for the most part things are okay. However I can't use compiz or any effects. When I try I lose all window borders. I think it is a problem with open gl and compiz. But even if I try to use the native ubuntu configuration utility I loose the widows borders. For the most part everything looks okay right now but I would love to solve the problem. I am going to paste the xorg-config. 

Until I build my new Pc I really need to use the large monitor but I would love to have things running normally.

I'm also attaching the xsesssion-error log. I think that will be more helpful than the config. file.
xorg-config

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by amedac on 2008-09-10
Try to install compiz fusion icon: ```
sudo apt-get install fusion-icon
```
For window borders is used emerald or GTK window decorator. Use emerald, and try to reload compiz few times. For me fusion-icon was great help.

Another thing, i installed compiz from git repository, more effects, and it's great.

---

### Post by overdrank on 2008-09-10
> **rocknzen said:**
> Last night the motherboard in my desktop went bad. So I had to set up my laptop which is an HP dv6110 with nvidia Go 6150 vid card. I wanted to use my 22" Samsung monitor in a twin monitor configuration (actually I don't care about using 2 monitors I just need the larger monitor for my work)
In any case I followed a how to guide to make it work ([http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)) and for the most part things are okay. However I can't use compiz or any effects. When I try I lose all window borders. I think it is a problem with open gl and compiz. But even if I try to use the native ubuntu configuration utility I loose the widows borders. For the most part everything looks okay right now but I would love to solve the problem. I am going to paste the xorg-config. 

Until I build my new Pc I really need to use the large monitor but I would love to have things running normally.

I'm also attaching the xsesssion-error log. I think that will be more helpful than the config. file.
xorg-config
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```
Hi and if you are not using Hardy then you may try this command 
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

---

### Post by rocknzen on 2008-09-10
I have the fusion icon and I am running Hardy

---

