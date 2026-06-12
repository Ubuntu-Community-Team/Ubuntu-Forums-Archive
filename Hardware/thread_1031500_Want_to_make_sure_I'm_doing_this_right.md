---
title: "Want to make sure I'm doing this right"
date: 2009-01-05
forum: Hardware
---

### Post by ZeroTruths on 2009-01-05
I have a Logitech VX Nano mouse and am trying to bind a custom command to the Scroll Wheel Tilt action. Here's my xorg.conf file as it is right now.
```
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
	Driver	"fglrx"
EndSection
Section "InputDevice"
  	Identifier  "VX Nano"
  	Driver      "evdev"
  	Option      "Name" "Logitech USB Receiver"
  	Option	    "Protocol" "evdev"
  	Option	    "Buttons" "9"
  	Option	    "SendCoreEvents" 
  	Option      "ZAxisMapping" "4 5"
    Option      "WAxisMapping" "8 9"
EndSection
```

What would be the next step to bind a command to the Tilting action?

---

