---
title: "Thinkpad 3rd button"
date: 2006-10-04
forum: Hardware &amp; Laptops
---

### Post by NetworkGuy on 2006-10-04
Hi All,

I have a thinkpad that was properly configured that the 3rd button on the touchpoint mouse was used to scroll the screen up and down.   Earlier this week, I installed a new theme and started using the gdesklet applets (app launcher only).

Now the 3rd button does nothing.  Here is the section for the mouse in my xorg.conf file

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"EmulateWheel"		"true"
	Option		"EmulateWheelButtton"	"2"
	Option		"Emulate3Buttons"	"true"
EndSection

``` 

Any idea what I need to look at to try and get this working again?  It's no big if I can't utilize the button anymore, but I want to know what broke it.  

Thanks all.

---

