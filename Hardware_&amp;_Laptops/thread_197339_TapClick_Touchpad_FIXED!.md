---
title: "Tap/Click Touchpad FIXED!"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by PWill on 2006-06-15
Ok, so I think we are all really dumb. The way people have been posting the code, is unreadable for X.org. It needs to be 

"Option"(Tab)(Tab)"whatever"(Tab)(Tab)"whatever"

For example, my xorg.conf looks like 
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"		"0"
	Option		"SHMConfig"		"on"
EndSection

```
All the extra stuff you need is:

Option(Tab)(Tab)"MaxTapTime"(Tab)(Tab)"0"

I had a few spaces instead of tabs in there, and thats what screwed it up. If you want to use qsynaptics, add that last line, that looks like this:
Option(Tab)(Tab)"SHMConfig"(Tab)(Tab)"on"

Any questions about this, email me at [email]xiamcitizen@gmail.com[/email]

---

