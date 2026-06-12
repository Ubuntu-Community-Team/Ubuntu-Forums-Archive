---
title: "Primary Screen, Laptop with external monitor"
date: 2008-09-06
forum: Hardware
---

### Post by yusuo85 on 2008-09-06
Ok im stuck, completely lost, I got a new monitor for my laptop today, plugged it in all is good, went to watch a movie and the movie would only play through the laptop screen not my monitor (sigh). Any help to resolve this issue would be greatly appreciated. Im using VLC and a copy of my xorg.conf is below, if anyone can help....

.........................................................................

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by yusuo85 on 2008-09-06
Ok im stuck, completely lost, I got a new monitor for my laptop today, plugged it in all is good, went to watch a movie and the movie would only play through the laptop screen not my monitor (sigh). Any help to resolve this issue would be greatly appreciated. Im using VLC and a copy of my xorg.conf is below, if anyone can help....

.................................................. .......................

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "gb"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Synaptics Touchpad"
EndSection

---

### Post by yusuo85 on 2008-09-06
Ok im stuck, completely lost, I got a new monitor for my laptop today, plugged it in all is good, went to watch a movie and the movie would only play through the laptop screen not my monitor (sigh). Any help to resolve this issue would be greatly appreciated. Im using VLC and a copy of my xorg.conf is below, if anyone can help....

.................................................. .......................

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "gb"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Synaptics Touchpad"
EndSection

---

### Post by overdrank on 2008-09-06
Please do not make multiple threads on the same issue. What is the model of the graphics card and have you tried the command ```
gksu displayconfig-gtk
``` and set up your additional monitor there.

---

