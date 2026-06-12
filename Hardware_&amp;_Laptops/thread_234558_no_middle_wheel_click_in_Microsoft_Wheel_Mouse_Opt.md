---
title: "no middle wheel click in Microsoft Wheel Mouse Optical USB"
date: 2006-08-11
forum: Hardware &amp; Laptops
---

### Post by ghee22 on 2006-08-11
Click on wheel, nothing happens.  This is the case for any program (Firefox, Epiphany).  If I click on left & right simultaneously, then it results as a middle click.

Here's my xorg.conf for mouse
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Buttons"		"5"
EndSection
```

How do I fix this?

---

