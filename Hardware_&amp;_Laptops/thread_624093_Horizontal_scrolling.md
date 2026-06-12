---
title: "Horizontal scrolling"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by Steve Fisher on 2007-11-26
OK, I know this has probably been covered a thousand times, but all the xorg.conf's I've seen vary slightly, and tbh I'm not exactly sure what I should or shouldn't be doing. So here's the relevant section of my xorg.conf ...

```


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
	Option		"HorizScrollDelta"	"20"
	Option		"HorizEdgeScroll"	"true"
	Option		"SHMConfig"		"true"
EndSection


```

I've added the "HorizEdgeScroll" entry, and also changed the value of "HorizScrollDelta" from 0 to 20, but it still isn't working. I know it *could* work, because it used to in Feisty (all it needed was GSynaptics, and it just worked...) and of course, it works in XP...

It's a Dell Latitude D505. I think there may be something fundamentally wrong with my xorg.conf, because this doesn't seem to add up:

```
cat /proc/bus/input/devices

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=mouse2 event4 
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003


```

Is it Alps or Synaptic? I'm confused....

---

