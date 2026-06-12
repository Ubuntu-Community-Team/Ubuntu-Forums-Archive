---
title: "[SOLVED] Acer 5920 Touchpad Difficulty"
date: 2008-08-22
forum: Hardware
---

### Post by degroof on 2008-08-22
I've got 8.04 (wubi) on an Acer 5920 with a Synaptics touchpad and a Logitech USB wireless mouse. Both the mouse and the touchpad work, up to a point. 

The thing is that nothing I do affects the behavior of the touchpad. All I really want is to disable tapping but nothing I've tried (tpconfig, synclient, gsynaptics) makes any difference. The only thing that affects it is hitting Fn-F7 to toggle the touchpad off and on, which isn't really what I want. 

One interesting thing is that **synclient -m 20** prints out only one line and then stops.

Any thought, suggestions?


My xorg.conf...

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"		"true"
	Option		"TapButton1"		"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```


And some info from Xorg.0.log...


```
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(**) Option "Device" "/dev/input/event10"
(**) Option "SHMConfig" "true"
(**) Option "TapButton1" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
...
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(**) Option "Device" "/dev/input/event10"
(--) Synaptics Touchpad touchpad found
```

---

### Post by degroof on 2008-08-22
Here's the one and only line printed from synclient:

```
synclient -m 20
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   0.000     0    0   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
```

---

### Post by errenay on 2008-08-26
Maybe this helps you:
[http://ubuntuforums.org/showthread.php?t=517156]("http://ubuntuforums.org/showthread.php?t=517156")
Then try again to disable tapping...

---

### Post by degroof on 2008-08-27
Thanks. Y'know, I read that thread earlier and thought I'd tried its suggestions. I must've missed a step somewhere, though. Tried again just now and everything's working perfectly. Even synclient is printing status info.

---

