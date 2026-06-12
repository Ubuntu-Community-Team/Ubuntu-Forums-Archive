---
title: "Need additional Monitor Resolution"
date: 2009-03-05
forum: Hardware
---

### Post by sagasha on 2009-03-05
I know resolution problems are asked time and again but I've searched and googled and can not resolve my problem.

I have a ViewSonic VA1926W 19" monitor and have the nvidia driver installed. It gives me the native resolution of 1440x900 and lookes great but I would love to have 1280x800, which is supported by my monitor and I use with my Windoze machine.

The options presented me by nvidia Xserver settings does not offer me this resolution, how in the world can I add it? "Nvidia Xserver settings" does show my correct monitor. I'm using 8.10. Thanks in advance.

Here is my xorg.conf

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

