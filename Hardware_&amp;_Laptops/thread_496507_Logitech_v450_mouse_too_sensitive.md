---
title: "Logitech v450 mouse too sensitive"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by Orvil on 2007-07-09
Hi all,

I recently bought a Logitech v450 for my laptop. Very nice mouse and all, but it's just **too** sensitive. I really have to concentrate when moving the mouse around.

Code from my xorg.conf listed below. The Logitech v450 section I got from doing [http://ubuntuforums.org/showthread.php?t=326101]("http://ubuntuforums.org/showthread.php?t=326101").

When I adjust the acceleration or sensitivity in *System* | *Preferences* | *Mouse* | *Motion*, it only affects the touchpad mouse.

I've tried setting the "Resolution" option to 400, 800 and 2000, doesn't seem to have any effect.

I would appreciate any ideas to what I might try next.

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option          "CorePointer"
	Option 		"Device" "/dev/psaux"
	Option 		"Protocol" "auto-dev"
	Option 		"HorizScrollDelta" "0&#8243;
	Option 		"SHMConfig" "on"
EndSection

Section "InputDevice"
        Identifier      "Logitech v450"
        Driver          "evdev"
        Option          "Name"                          "Logitech USB Receiver"
        Option          "Dev Phys"                      "usb-0000:00:1d.2-2/input0"
        Option          "HWHEELRelativeAxisButtons"     "7 6"
        Option          "SendCoreEvents"                "true"
	Option		"Resolution"			"2000"
EndSection

```

---

### Post by Orvil on 2007-07-12
Think I've managed it.
Here are the relevant sections in my xorg.conf.
I added the SendCoreEvents option to my touchpad and set the logitech mouse to be the corepointer in the ServerLayout section. The touchpad didn't work without the SendCoreEvents in the touchpad section.
Now when I change sensitivity/acceleration settings in *System* | *Preferences* | *Mouse* | *Motion* it affects my logitech, I guess this is because it is now the CorePointer.
Hope someone finds this useful. :)

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	**[COLOR="Red"]#Option          "CorePointer"[/COLOR]**
	Option 		"Device" "/dev/psaux"
	Option 		"Protocol" "auto-dev"
	Option 		"HorizScrollDelta" "0&#8243;
	**Option		"SendCoreEvents"                "true"**
	Option 		"SHMConfig" "on"
EndSection

Section "InputDevice"
        Identifier      "Logitech v450"
        Driver          "evdev"
        Option          "Name"                          "Logitech USB Receiver"
        Option          "Dev Phys"                      "usb-0000:00:1d.2-2/input0"
        Option          "HWHEELRelativeAxisButtons"     "7 6"
        Option          "SendCoreEvents"                "true"
	Option		"Resolution"			"2000"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Synaptics Touchpad"
	InputDevice	"Logitech v450" **"CorePointer"**
	InputDevice	"Configured Mouse"
EndSection

```

---

### Post by ikus060 on 2007-09-18
I follow your guide and it's work perfectly on my thinkpad T43 with a logitech V450.

Thank !

---

### Post by kevinzhang on 2008-04-09
I want to buy a V450 and I am not very sure about it can working well on Ubuntu before I see your post, Thanks!

---

