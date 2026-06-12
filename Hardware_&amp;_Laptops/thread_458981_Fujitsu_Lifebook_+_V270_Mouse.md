---
title: "Fujitsu Lifebook + V270 Mouse"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by hunkybill on 2007-05-30
Hi,

Fujitsu e8210 Lifebook with built-in Bluetooth, Logitech V270 Mouse. The mouse works with Ubuntu Feisty, albeit it is not very responsive. It seems as though there is some competition between the mouse polling and some other system resource? 

The mouse has moments of lag, overshooting, and just feels like crap compared to my USB mouse (now uninstalled). Is there anyway I can get a bluetooth mouse debugged?. I have very little idea of what to check for, other than the mouse configuration in xorg.conf. I am very close to giving this hardware the boot but I am holding out hope that the fix is possible and that Logitech V270 can be used with my laptop.

My xorg.conf relevant sections are included here. Any tips most appreciated. I am pretty sure the Bluetooth is working fine, but perhaps there are some issues to be addressed there? I am not sure at all if there are any configurable settings for that.

```
Section "ServerLayout"
	Identifier	    "Default Layout"
  	screen 		   0    "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Bluetooth Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
```

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Protocol" "ExplorerPS/2"
	Option		"Device"  "/dev/input/mice"
	Option		"Emulate3Buttons" "true"
	Option		"ZAxisMapping" "4 5"
EndSection

Section	"InputDevice"
	Identifier	"Bluetooth Mouse"
	Driver		"mouse"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping" "4 5"
EndSection

```

Thanks

---

