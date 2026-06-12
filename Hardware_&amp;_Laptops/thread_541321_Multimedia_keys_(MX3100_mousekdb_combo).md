---
title: "Multimedia keys (MX3100 mouse/kdb combo)"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by kayrune on 2007-09-02
I'm having problem getting all my multimedia keys to work, so far I'm pretty close.
The ones I'm missing is the following:

FastForward
FastBack
Media
Mute 
Volumecontrol <<< Really miss this one !!
Play/pause
Stop
Email
Calc

So basically, those missing are those I use the most :(


This is the xorg.conf settings:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"evdev"
        Option          "Device"  "/dev/input/event1"
	Option		"CoreKeyboard"
	**Option		"XkbLayout"	"no+inet(evdev)" #no for norwegian kbd**
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event2"
EndSection
```

With my limited knowledge I'm thinking the **bold** line is the one that has to be tweaked, but I have no idea where to look for alternative options.

I'm running Gutsy 64bit..

---

