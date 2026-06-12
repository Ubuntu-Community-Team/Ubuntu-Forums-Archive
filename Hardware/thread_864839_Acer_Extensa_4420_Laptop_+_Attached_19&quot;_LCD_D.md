---
title: "Acer Extensa 4420 Laptop + Attached 19&quot; LCD Display"
date: 2008-07-20
forum: Hardware
---

### Post by SuperMike on 2008-07-20
I have a new Acer Extensa 4420 laptop with Ubuntu 8.04. I also have a 19" attached LCD panel that's square-ish, not a widescreen like this laptop. My laptop can handle a screensize of 1280x800 (refresh 60hz), while my attached flat-panel LCD monitor can handle 1280x1024 (refresh 75hz).

My end goal is to have things such that I close my laptop lid, the laptop stays running, and I drive a separate monitor and use a regular mouse and keyboard. That way, I can take my laptop on the go when I need to, but can pound away on much more durable hardware most of the time.

There are few problems I'm having:

* The Fn+F5 key won't toggle displays back and forth. Probably would work in Vista, but doesn't look like it has any effect on Ubuntu.

* I can attach a separate monitor, but the video comes up at no larger than what the laptop screen can handle. It would be great if my laptop was one size and the attached monitor were another.


NOTE: I do know a thing or two about xorg.conf editing.


Where do you suggest I start to fix this problem?

---

### Post by SuperMike on 2008-07-20
I managed to get something sort of working, except that 'metacity' (the thing that draws proper cursors and titlebars/window decorations) is not loading properly. I have to open a command prompt and do "metacity &" (no need for sudo) in order to make it okay, and then minimize that window. The moment you close that window, it turns off metacity again.

Anyway, the trick is to do this:

$ sudo aticonfig --initial=dual-head

Then, go in and edit your /etc/X11/xorg.conf's ServerLayout area to be:

Option "Xinerama" "off"
Option "Clone" "on"

Then log out and back in again.

I noticed when I opened the Display Resolution control panel in one screen, it was completely different than it would be to open in the other screen. I would have thought it would give me two screens in the same control panel, but it did not. Anyway, I also noticed that it gave me optimal resolution, color depth, and display hertz in each screen.

So, besides the metacity bug, it also turns off any 3D Compiz visual effects you may have had enabled.

Anyway, this will do for now and when I go on the road with the laptop, I can swap my original /etc/X11/xorg.conf file with the original one, and vice-versa.

---

### Post by SuperMike on 2008-07-20
For some strange reason, the metacity bug just went away all on its own. I don't understand why.

Another odd side effect is that I can't drag windows between the two screens. If I open a window on a given screen, it remains there. I can move my cursor between the two -- just not move a window between the two.

My xorg.conf file looks like:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	Screen         "aticonfig-Screen[1]" LeftOf "Default Screen"
	InputDevice    "Synaptics Touchpad"
	Option		"Xinerama" "off"
	Option		"Clone" "on"
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
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
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

---

### Post by SuperMike on 2008-07-20
I came back after letting my laptop and attached monitor run for awhile. The X server must have crashed because the mouse was working on both screens, but clicks were unresponsive. The attached monitor screen had visible content, but the laptop had gone black except for the white cursor that was present. So more than likely some kind of screen blanking must cause a lockup.

---

### Post by SuperMike on 2008-07-21
The X crash bug is fixed if you install Envy:

apt-get install envyng-gtk

Then, let it autodetect the proper ATI driver and let it reboot. At that point, it seems to no longer have a screen lockup issue after power management kicks in.

The downside? Yeah, logging out seems to hang up and I have to kill it with CTRL+ALT+BACKSPACE when possible, or hard-kill it (Fn+Power) when that fails.

---

### Post by SuperMike on 2008-07-24
After installing Envy, my lockups after coming out of power saving idle went away. But then I started getting lockups on logout. Well, this is now resolved. I went into Launchpad to file a bug report and they responded with the resolution:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/251373](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/251373)

---

