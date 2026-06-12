---
title: "[SOLVED] Latitude C640 Touchpad Pulls to Lower Left"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by dtreichler on 2008-02-19
I've just finished installing Gutsy on an old Dell Latitude C640 but I'm having a big problem with the touchpad.  As long as it's activated, the cursor pulls hard to the lower left corner of the screen... it's like there's a very large negative velocity applied to it.  If I disable the touchpad in the BIOS and plug in a PS/2 mouse, the cursor is fine.

I've played around with xorg.conf a bit but haven't really gotten very far.  This is my first experience with Ubuntu on a laptop so I'm in a little over my head.

If you've got any ideas, I'm listening.

My xorg.conf file is basically stock from the install, but I'll post it here.

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

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
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

```

---

### Post by dtreichler on 2008-02-28
For those of you stumbling upon this hoping for a fix, here you go:

If you happen to have a Dell Latitude C6xx laptop, it turns out it's a hardware issue.  I stumbled upon a previous thread: [http://www.ubuntuforums.org/showthread.php?t=345686]("http://www.ubuntuforums.org/showthread.php?t=345686").

The jist of it is this:
> 
Find the service manual online and follow the instructions to get your keyboard loose. Once you remove the screws on the bottom of the laptop it will be held on by the data cable for the keyboard and nipple. Pull the data cable off and inspect it. You should see a large ribbon and a small ribbon feeding into a plastic connector. The connector can be pried apart by the ends with a small flathead screwdriver. Once apart, pull the smaller ribbon out of the connector, then reassemble it. Plug the connector back into the motherboard, leaving the little ribbon free. Reattach the keyboard and boot up. The wandering mouse should be gone!


To remove the keyboard (at least if you have a C640), follow Dell's service manual: [http://support.dell.com/support/edocs/systems/latc640/sm_en/keyboard.htm]("http://support.dell.com/support/edocs/systems/latc640/sm_en/keyboard.htm").

That's all it takes! Just be gentle when separating the connector. I was a little too rough and managed to break off some small tabs. Thankfully everything holds together, albeit not quite as tight.

Hope that helps!

---

