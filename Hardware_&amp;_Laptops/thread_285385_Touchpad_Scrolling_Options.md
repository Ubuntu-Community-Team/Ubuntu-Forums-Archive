---
title: "Touchpad Scrolling Options"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by leetcharmer on 2006-10-26
I have a laptop touchpad that doesn't work out of the box in edgy 6.10.
Problems:

1) Double-Tap is on
2) Scrolling is off

Semi-Fixes:

To get the synaptic scrolling on, I need to update the xorg.conf from:

```
Section "InputDevice"
Identifier	"Configured Mouse"
Driver		"mouse"
Option		"CorePointer"
Option		"Device"		"/dev/input/mice"
Option		"Protocol"		"ExplorerPS/2"
Option		"ZAxisMapping"		"4 5"
Option		"Emulate3Buttons"	"true"
EndSection
```

to:

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "synaptics"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "SynPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection
```

The problem here is that, it turns on both Horizontal and Vertical scrolling.  I would only prefer Vertical, as horizontal is not on my mouse and causes problems (like going back and forth between windows accidentally).

Also, I would like to turn double tap off .. or at least, make it MUCH less sensitive.  Any clues to how I can accomplish this?  Thanks :D

---

### Post by leetcharmer on 2006-10-26
By running: sudo dpkg-reconfigure xserver-xorg
I was able to remove the Horizontal Scrolling -- it created two sections

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```

The Double Tapping is still too sensitive/on, and I would like that turned off.  Also, is it possible to tweak the horizontal scroll area?  It glurshes over the allocated space on my touchpad, which is highly annoying.  I need to crop it some on the left.

---

### Post by stenka on 2006-10-27
I am not sure to have the same issue.
My issue look more like this one :
[http://www.ubuntuforums.org/showthread.php?t=275564&highlight=touchpad](http://www.ubuntuforums.org/showthread.php?t=275564&highlight=touchpad)

I reported a bug :
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68540](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68540)

Please let me know if you have any idea about it.

---

### Post by noodles12 on 2006-11-05
> **leetcharmer said:**
> I have a laptop touchpad that doesn't work out of the box in edgy 6.10.
Problems:

1) Double-Tap is on
2) Scrolling is off

Semi-Fixes:

To get the synaptic scrolling on, I need to update the xorg.conf from:

```
Section "InputDevice"
Identifier	"Configured Mouse"
Driver		"mouse"
Option		"CorePointer"
Option		"Device"		"/dev/input/mice"
Option		"Protocol"		"ExplorerPS/2"
Option		"ZAxisMapping"		"4 5"
Option		"Emulate3Buttons"	"true"
EndSection
```

to:

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "synaptics"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "SynPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection
```

The problem here is that, it turns on both Horizontal and Vertical scrolling.  I would only prefer Vertical, as horizontal is not on my mouse and causes problems (like going back and forth between windows accidentally).

Also, I would like to turn double tap off .. or at least, make it MUCH less sensitive.  Any clues to how I can accomplish this?  Thanks :D

I did this and my scroll on my touchpad works awesome! However, my usb mouse no longer works anymore. Have you run into this problem?

---

### Post by noodles12 on 2006-11-15
Has anyone had this problem? I have to edit the xorg.conf and restart to switch to use my usb mouse.

---

