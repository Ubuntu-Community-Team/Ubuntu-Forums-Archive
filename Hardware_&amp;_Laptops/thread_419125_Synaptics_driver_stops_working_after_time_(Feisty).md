---
title: "Synaptics driver stops working after time (Feisty)"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by Fluxid on 2007-04-22
Hi!
I have problem with my synaptics touchpad.
After some time of working my touchpad started to behave differently. Scrolls, multi-finger taps, tap-and-hold-to-drag, and other features stopped to work. Also sensitivity has changed. For me it looked like normal mouse driver started to work instead of synaptics.
(Also my touchpad sometimes slow-downs, taps even when my finger dont leave surface, or cursor unexpectedly flies half a screen away, but it's not worst thing now)
After switching screen by ctrl+alt+f1 (oh, yeah, i've got colorful stripes instead of terminal...) and then switching back it started to work correctly, but after time it crash again.

After total reconfiguration and experimenting with xorg.conf, after time my touchpad stops to work at all. Again, i have to reset X (switch to terminal or relog) to use touchpad.

I tried /dev/psaux and /dev/input/mouse1
i tried auto-dev, raw
i tried to remove "Configured mouse"
i tried to change order of loading pointers (synaptics before configured)
i exprimented with CorePointer, AlwaysCore and SendCoreEvents in many ways

My config:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Synaptics Touchpad"
	InputDevice    "Configured Mouse"
EndSection

...

Section "Module"
...
	Load	"synaptics"
EndSection

...

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"CorePointer"
#	Option		"Device"		"/dev/psaux"
	Option		"Device"		"/dev/input/mouse1"
#	Option		"Protocol"		"auto-dev"
	Option		"Protocol"		"raw"
	Option		"SHMConfig"		"1"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

/proc/bus/input/devices:
```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 event0 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

...

I: Bus=0011 Vendor=0002 Product=0007 Version=0000
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input12
H: Handlers=mouse1 event8 ts1 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003
```

Fragment of log:
```
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "SHMConfig" "1"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(**) Option "CorePointer"
(**) Synaptics Touchpad: Core Pointer
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SynapticsCtrl called.
SynapticsCtrl called.
SynapticsCtrl called.
Synaptics DeviceOff called
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event8
(**) Option "Device" "/dev/input/event8"
(--) Synaptics Touchpad touchpad found
Synaptics DeviceOff called
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
Synaptics DeviceOff called
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event8
(**) Option "Device" "/dev/input/event8"
(--) Synaptics Touchpad touchpad found
```

It doesn't matter, is it Xgl or Xorg
I have latest synaptics drivers available (0.14.16-0ubuntu7)
Before installing Feisty, my touchpad worked perfectly.

Any ideas?

---

### Post by inchaos on 2007-04-25
Those are the exact problems I'm having with mine.
Using an HP Pavilion dv5000.
I thought maybe it was a hardware problem and was just going to get a USB mouse.  It's really bizarre, when I first boot it works fine but then the scrollbar feature stops functioning and I get lags, random taps when I SWEAR I haven't tapped the pad, and the pointer jumping all over the place.
I'm kind of a beginner, if there is a fix for this, I'd love to know about it.

---

### Post by strabes on 2007-04-25
Here's a page with all of the options you can put into your xorg.conf for synaptics touchpads: [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

Just experiment.

---

### Post by Fluxid on 2007-04-26
I've added those modules to load on boot... i'll see what happen...

---

### Post by woodwardmw on 2007-04-26
> **inchaos said:**
> It's really bizarre, when I first boot it works fine but then the scrollbar feature stops functioning and I get lags, random taps when I SWEAR I haven't tapped the pad, and the pointer jumping all over the place.
I'm also using a HP dv5000 and have exactly these problems.

---

