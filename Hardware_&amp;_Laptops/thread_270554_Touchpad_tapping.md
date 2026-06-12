---
title: "Touchpad tapping"
date: 2006-10-03
forum: Hardware &amp; Laptops
---

### Post by miyumi on 2006-10-03
Not sure if this is the right forum for this...

I have a Gateway laptop, and my mouse tapping is driving me nuts. It'll tap the okay when I'm typing in my password, leaving me reloading the page again and again. It will keep switching my windows on me, so I have to keep switching back. It's even jumped and then closed a tab in firefox on me, mid-post. How do I disable the tap? (Yes, I've already done a google search and tried the most promising suggestions found, none of which worked.) Any help will be greatly appreciated, even a useful link. Thanks in advance.

-Miyumi

---

### Post by hw-tph on 2006-10-03
It depends on what type of touchpad you have. If you have a Synaptics or Alps touchpad you're using the synaptics driver. The synaptics X input driver provides tons of settings for fine tuning the behaviour of the touchpad. The one you are most likely looking for is "MaxTapTime". Set it to "0" and tapping should be disabled.

Note that the Ubuntu xorg.conf will have several mouse entries - edit the one that is actually controlling the behaviour of the touchpad. With any one of the two touchpad types I mentioned above you can identify the correct section by the driver used - "synaptics". Here is my Alps touchpad section - with tapping disabled (I *hate* tapping but understand some people can actually use it...).
```
Section "InputDevice"
    Identifier  "Synaptics Touchpad"
    Driver      "synaptics"
    Option      "SendCoreEvents"    "true"
    Option      "Device"        "/dev/psaux"
    Option      "Protocol"      "auto-dev"
    Option      "HorizScrollDelta"  "0"
    Option      "MaxTapTime"    "0"
EndSection
```


Håkan

---

### Post by miyumi on 2006-10-03
Maybe this will help... the only mouse listed in my config is

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

No touchpad listed...

---

