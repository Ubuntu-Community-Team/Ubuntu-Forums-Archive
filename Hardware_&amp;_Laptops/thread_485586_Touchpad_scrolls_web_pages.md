---
title: "Touchpad scrolls web pages"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by kevmore on 2007-06-27
Does anybody know how to make my touchpad stop scrolling the page.  I have a scroll panel on the right of the touchpad that is supposed to do the scrolling.  It is very annoying to try and move the cursor to click on a link and the whole screen is moving up and down.  I have read most of the posts that have to do with touchpads.  Thanks in advance.

Kevin.

---

### Post by olejorgen on 2007-06-27
If you have a synaptics touchpad, you could install **gsynaptics** and add 
```
Option "SHMConfig" "true"
``` under you synaptics inputdevice section.
e.g.
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SHMConfig"             "true"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

```
After a X restart you can run gsynaptics and disable vertically scrolling.

Or you could read up on synaptics and figure out what to put in xorg.conf so you don't have to install gsynaptics.

---

