---
title: "Gsynaptics, how can I?"
date: 2008-12-31
forum: Hardware
---

### Post by RodrigoRodrigues on 2008-12-31
I have a Tx2510us, it is a war to make things work on it, each piece of hardware need a lot of google to work,

I am using Ubuntu 8.10

when I start gsynaptics I get the message:
[I]"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"[/I]

But in my xorg there is no section Synaptics... I tried to add it but doesn't work... I add these lines:


Section "InputDevice"
	Identifier	"Synaptics Pad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
        Option          "SHMConfig"     "true"
	Option		"HorizEdgeScroll"	"0"
	Option		"CircularScrolling"	"True"
	Option		"CircScrollTrigger"	"8"
EndSection


I copied it from google...
this seems to be easy to solve. I found a lot o people with the same problem, but I am the only one who didnt have this section in xorg.config

---

