---
title: "Use External Display with Laptop"
date: 2008-07-14
forum: Hardware
---

### Post by burgerearl on 2008-07-14
Hi,

I have a dell Inspiron 1520 and an external monitor. With my current setup I prefer to use the external monitor. The monitor has been correctly detected and is using its maximum resolution, however the laptop LCD is still on and is set to the same resolution as the external monitor, thus showing only a portion of the screen.

My first preference would be to just have the laptop screen go blank, but I would also be interested in learning how to correctly configure a dual monitor setup.

A couple other notes: the function key (Fn+F8, for me) that switches between external and internal LCD output in Windows does nothing that I've noticed - I'd love to know how to set that up.

I'm also not certain that my video setup can support dual monitors - I haven't successfully set that up in Windows (although I haven't put much effort in to it).

Thanks for any help!

Jake

Here's a (hopefully) relevant section of xorg.conf:

```
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option		"AllowGLXWithComposite"	"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection
```

---

