---
title: "Touchpad scrolling resolution and weird two finger scroll behavior"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by chiefrocka on 2007-10-31
Hi all,

I've been struggling with these issue for a few days now:

1. I'd like to change how many lines my touchpad scrolls by when I use the vertical scroll feature of my touchpad (the scroll area on the right edge of my touchpad). The default is that with every "scroll tick", the document/webpage scrolls by 3 lines. I'd like to change this to 1 or maybe even half a line so I can get a smooth motion. I checked all the options in the man page of "synaptics" but none of the options specify how many lines are scrolled. VertScrollDelta sounds like the closest thing, but it's just measuring how much your finger should move before generating a "scroll tick".

2. I have enabled two-finger scrolling, but my touchpad has some weird behavior. When ever I move my two-fingers across the touchpad, the page begins to scroll in the correct direction, but then it coasts (I have set the CoastingSpeed to 0 in xorg.config). Not only does it unwantedly coast, but when it coasts to the end of the page, it starts coasting back to its original location. Sometimes I can avoid this by not letting my two-fingers off the touchpad after I move them across, but instead, take them off of the touchpad (after scrolling) one finger at a time. This is a pain when I would like to rapidly scroll down a page.

Specs:
+ Ubuntu 7.10 Gutsy Gibbon
+ Synaptics touchpad driver (xserver-xorg-input-synaptics)
+ Compaq Presario V2140US (V2000 model)

Here is a copy of the touchpad section of my xorg.config file:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"CoastingSpeed"		"0"
	Option		"VertTwoFingerScroll"	"true"
	Option		"SHMConfig"		"on"
EndSection

```

---

### Post by WaySensei on 2007-12-18
I am having the same issue on a Macbook Pro running Gutsy. It is very annoying to have to be so conscious about my scrolling technique to avoid coasting. If you discover a fix to this, please let me know. Likewise, I will let you know if I find one. I am going to browse through the synaptics man page tonight.

---

### Post by buccaneere on 2007-12-19
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

Might or might not have info for you here. I found it looking into vertical scroll region adjustment...

---

