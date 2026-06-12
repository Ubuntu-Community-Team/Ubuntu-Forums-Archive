---
title: "Getting middle mouse button (wheel) and scroll to work!"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by Antioch on 2007-04-20
I have a 3 button mouse attached to my system (Feisty) with a mouse wheel. If I roll the whell the current document scrolls. However, in windows if you depress the wheel and at the same time move the mouse up or down the current document will scroll as well.

I prefer this method and I'm trying to figure out how to enable it, but I can't seem to find any relevant information.

Thank you.

---

### Post by Skidpad on 2007-04-21
Try searching for "cruise control", most people use that term to describe the function you are referring to.  What mouse is it?

---

### Post by Antioch on 2007-04-21
Just some standard Logitech USB mouse - nothing fancy. 2 buttons and a wheel.

Thanks for that name though, I'll search for it.

---

### Post by robenroute on 2007-04-21
What does the mouse section in your xorg.conf say? (you can file this file in /etc/X11)

---

### Post by Antioch on 2007-04-21
Well, it's on my T60 ThinkPad laptop, but I have a USB mouse plugged in.

The xorg.conf says:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```

I hope you can tell me how to fix it =)

---

### Post by velja27 on 2008-05-03
Well i found the way to enable that but only in Firefox.
U have to go and type about:config in url then find general.autoScroll
and set it to true.

---

