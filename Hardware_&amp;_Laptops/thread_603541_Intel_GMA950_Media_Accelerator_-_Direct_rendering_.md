---
title: "Intel GMA950 Media Accelerator - Direct rendering problems."
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by suupaabaka on 2007-11-05
I wanted to test out the capabilities of my laptop's (Benq R55U) graphics capabilities; I already run compiz, so I thought I'd see how it fared in a game. I chucked on Jedi Knight 2 through Wine, since it was the first game I picked up out of the box. Ran beautifully.

Feeling quite happy, I threw on a native Linux game, Urban Terror. To my complete suprise, the framerates were mostly around 9fps, unless I looked in a certain direction or down at the ground. Now, I'm not much of a gamer anymore, but even I could tell there was something wrong here.

I opened up a terminal and typed in 

```
glxinfo | grep direct
```

because that's one of the first things that came up through my forum search. The result was this:

```
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
```

Some more research (I'm not a gamer, but I'm one of those people who wants their system working at its peak) left me with an xorg.conf that looks like this:

```
Section "Module"
	Load		"glx"
	Load		"dri"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option		"DRI"
EndSection
```

and still no progress. I also substituted the "intel" bit above with "i810" to see if a different driver would make a difference, but no such luck. 

Any advice you guys could provide would be much appreciated! Thank you!

---

### Post by marksman on 2007-11-05
thenk you

---

### Post by suupaabaka on 2007-11-05
> **marksman said:**
> thenk you

You're welcome? Hehe, I hope my tinkering has helped you out.

An update: I removed all the xserver-xorg-video  drivers except for i810 and 915resolution., Still no luck :(

Are there any programs that would let me directly manipulate my graphics driver/chipset?

---

