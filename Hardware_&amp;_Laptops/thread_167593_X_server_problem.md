---
title: "X server problem"
date: 2006-04-28
forum: Hardware &amp; Laptops
---

### Post by alain.hegel on 2006-04-28
This seems to be a semi-common problem but I haven't found a definitive answer to it from browsing the forums. I suppose it's because I recently did a **sudo apt-get upgrade** but my X server no longer works and I always get bumped back to the command line in my subsequent attempts to start it.

Here's is the error message I receive:

```

(EE) No Input driver matching `kbd'
(EE) No Input driver matching `mouse'
(II) Synaptics touchpad driver version 0.13.6
Synaptics Touchpad no synaptics event device found (checked 1 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(WW) No core pointer registered
No core keyboard

Fatal server error:
failed to initialize core devices

```

I tried, but to no avail:
```
sudo dpkg-reconfigure xserver-xorg
```

Here is my current xorg.conf, or at least the section that concerns the problem

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
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

I'm not exactly sure what to change in xorg.conf to stop the problem. It certainly seems like a driver problem, I just don't know how to approach it.

Any assistance is greatly appreciated. Thanks.

---

### Post by alain.hegel on 2006-04-28
I solved the problem. I'm going to write what I did so future newcomers will have this as a guideline.

I have an IBM laptop btw. T30.

My first attempts after logging into root were:
```

apt-get install xserver-xorg-input-mouse
apt-get install xserver-xorg-input-kbd

```

Both however were up to date. So I moved on to solve the synaptics problem by doing this:

```

apt-get install xorg-driver-synaptics

```

Then I rebooted. The problem was still there but this time I got something in the line of:

```

Failed to load module "ati"

```

So I just 

```

apt-get install xserver-xorg-driver-ati

```

Rebooted once again and voila. Everything is back to normal.

---

