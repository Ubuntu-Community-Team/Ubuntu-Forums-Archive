---
title: "Small mouse annoyance."
date: 2005-07-18
forum: Hardware &amp; Laptops
---

### Post by chaumurky on 2005-07-18
I have an Logitech iFeel USB mouse which works well. There's just one small thing - when I boot up, the left/right mouse buttons don't respond until I click the mouse wheel. It's small but annoying. Anyone else get this? Here's the mouse section in my (automatically configured on install) **xorg.conf** if it helps anyone:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
``` 
 


- maybe there's a more suitable "protocol" line, or should I switch 3 button emulation off?

---

