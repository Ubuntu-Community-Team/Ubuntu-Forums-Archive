---
title: "Thinkpad T400 with 30-inch monitor latency issues"
date: 2008-10-08
forum: Hardware
---

### Post by colonhyphenp on 2008-10-08
I've got a Lenovo Thinkpad T400 laptop with an ATI HD Mobility 3470 graphics card running Ubuntu 8.04, and I'm having some latency issues when the laptop is connected to a 30 inch monitor.

First, more details on my setup:  The laptop is docked in a Lenovo Advanced Mini Dock.  This exposes a Dual link DVI port, which is powering the 30 inch display.  The machine also has an Intel integrated graphics card and support for "switchable" graphics, but I disabled both the card and OS detection of switchable graphics in the BIOS.  

I installed the proprietary ATI "fglrx" driver via the Hardware Drivers menu, and after running:

```

sudo aticonfig --initial=dual-head --screen-layout=right

```

and restarting X, GDM and Gnome start up normally, and both the laptop's 1440x900 screen and the external 30-inch monitor at 2560x1600 are powered.

However, there are some pretty bad latency problems when I move windows around on the 30 inch display... Specifically, when I move a window, or scroll down on a web page in Firefox, the screen takes a few seconds to repaint the new contents.  Resizing a window doesn't seem have the latency issues, nor does typing. Also, moving windows around on the laptop's 1440x900 screen behaves normally.

Here's what my xorg.conf file looks like... Anyone have any suggestions for fixing these latency problems?
```


Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
	Option	    "SHMConfig" "on"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option	    "TexturedVideo" "off"
	Option	    "EnableMonitor" "lvds,tmds1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```

Thanks

---

### Post by colonhyphenp on 2008-10-10
Bumped.

---

### Post by sse on 2008-10-18
Hi,

I have exactly the same setup, though I'm using my 30" solely while in dock and haven't tried dual head yet.

Works great with 8.10 beta with all the latest updates.
Even fglrx is out now for the new x server.
It's still a bit sluggish with compiz enabled, eg. Google Maps in Firefox in fullscreen, but definitely workable.

I didn't have to setup anything in xorg.conf.

PS: I've set the graphics option to "discrete" in the BIOS

---

### Post by colonhyphenp on 2008-10-30
Upgrading to 8.10 and getting the new fglrx fixed it for me - thanks a bunch!

---

