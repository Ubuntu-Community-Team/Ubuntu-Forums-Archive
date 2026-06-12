---
title: "Xorg display configuration(8.10)"
date: 2009-01-03
forum: Hardware
---

### Post by ligerzero459 on 2009-01-03
I just switched my laptop from Windows to 8.10 and when I first logged in, I found out my screen resolution was only 800x600, with no way to increase it. I've read a lot about modify in the xorg.conf file to include new display modes, but every time I try, I get an error when I reboot. Here's the current file that works:

```
Section "Device"
	Identifier "Configured Video Device"
	Driver "vesa"
	BusID "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier "Configured Monitor"
	DisplaySize 212 159
	Modeline "1024x768_61.00" 64.11 1024 1080 1184 1344 768 769 772 795 -HSync +Vsync
EndSection

Section "Screen"
	Identifier "Default Screen 1"
	Device "Configured Video Device"
	Monitor "Configured Monitor"
	DefaultDepth 24
EndSection
```

My question is, where do I put in the subsection to create new resolutions?

---

### Post by Ahadiel on 2009-01-03
What video card do you have? It may just be as simple as installing drivers for it.

System => Adimistration => Hardware Drivers

---

### Post by ligerzero459 on 2009-01-03
Actually, I'm not quite sure. It's an old laptop that I got from a friend and so I don't know the specs on it at all. I think it's a Trident

---

