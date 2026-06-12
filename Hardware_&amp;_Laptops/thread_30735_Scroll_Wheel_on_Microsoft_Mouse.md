---
title: "Scroll Wheel on Microsoft Mouse"
date: 2005-04-30
forum: Hardware &amp; Laptops
---

### Post by dfghost on 2005-04-30
I have a microsoft intellipoint optical scroll wheel mouse.  the three buttons work fine, but the scroll wheel does nothing.  I know that you can use the scroll wheel because a server at my school has Hoary and a scroll wheel mouse and it works fine.  So, any suggestions?  Thank's in advance.

---

### Post by 23meg on 2005-04-30
can you post the contents of the InputDevice sections in your /etc/X11/xorg.conf file? mine looks like this, and everything's fine:

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"

---

