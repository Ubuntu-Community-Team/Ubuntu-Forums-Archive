---
title: "Bluetooth Mouse scroll wheel stoped working."
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by lightchaser on 2008-04-14
I'm pretty new to Ubuntu, but its been a smooth transition.

I have a Microsoft 5000 Bluetooth Mouse that I haven't had a problem with until it just stopped working this afternoon. It functions normally when I use the button (to rotate desktop cube, close tab in  Firefox etc), but I am no longer able to scroll down a page. 

I booted into Vista and it its completely functional.

From what little I know it all looks as it should in the xorg.conf

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Thanks in advance for any help.

---

