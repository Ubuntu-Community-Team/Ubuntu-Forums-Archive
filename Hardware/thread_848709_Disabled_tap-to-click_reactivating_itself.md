---
title: "Disabled tap-to-click reactivating itself??"
date: 2008-07-03
forum: Hardware
---

### Post by rapper97 on 2008-07-03
I found out [how to disable touchpad = click by setting [font="monospace"]MaxTapTime[/font] to [font="monospace"]0[/font]]("http://ubuntuforums.org/showthread.php?t=421236"), but now, it's intermittently being re-enabled! I have no idea what I'm doing to trigger this, but I know that occasionally I'll be typing and the cursor will get put in the wrong place, or if I touch the trackpad wrong, whatever window I'm over becomes active, and tap to click has been automatically turned on. When I restart the computer (probably if I just restart Xorg, too), "tap as good as click" is once again off... but how do I keep this from rearing its ugly head again? I've included the relevant bits of my [font="Monospace"]xorg.conf[/font] file; maybe something is conflicting?

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"MaxTapTime"		"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
```

---

