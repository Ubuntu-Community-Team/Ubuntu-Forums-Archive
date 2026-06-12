---
title: "synaptic scroll backwards"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by jmmert on 2007-04-24
I'm running Xubuntu 7.04 on Fujitsu lifebook and most things are working except the scroll button at the Synaptic touchpad is backwards. when I want to scroll down it scrolls up and down when I want to go up it scrolls down. I've install gsynaptics but that has no settings for that. The touchpad vertical scrolling works fine but I prefer the button.

---

### Post by strabes on 2007-04-24
Post the output of this command: ```
cat /etc/X11/xorg.conf
```

Can you clarify what you mean by this sentence: > The touchpad vertical scrolling works fine but I prefer the button.

---

### Post by jmmert on 2007-04-24
here's the xorg, the vertical scroll zone on the touchpad itself works correctly not the extra button between the left and right buttons.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
EndSection

---

