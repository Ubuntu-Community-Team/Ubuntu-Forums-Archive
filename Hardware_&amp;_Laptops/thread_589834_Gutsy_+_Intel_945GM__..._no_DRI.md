---
title: "Gutsy + Intel 945GM  ... no DRI?"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by ljp37 on 2007-10-24
Hello,

I've just upgraded to Gutsy, and DRI doesn't work anymore with my Intel 945GM Express chip.  Running "dpkg-reconfigure xorg-xserver" allowed me to get 1920x1200 resolution working on my external Dell 2405, but I just can't seem to get DRI using i810 or intel drivers.

Please, could someone with a working (Intel 945 + 1920x1200 + DRI) post their xorg.conf?

Oddly, the xorg log indicates that things are just fine:

  (II) I810(0): [drm] installed DRM signal handler
  (II) I810(0): [DRI] installation complete
  (II) I810(0): [drm] dma control initialized, using IRQ 22
  (II) I810(0): direct rendering: Enabled

but I get this when I run glxinfo, even as root:

$ glxinfo |grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

glxgears causes X to crash.

This all used to with Feisty, but I foolishly forgot to save my xorg.conf.  Please, someone, help!

---

### Post by ljp37 on 2007-10-25
Nevermind.. it's fixed.  

I did this:

  apt-get remove .*mesa.* .*xorg-xserver.*

  apt-get install ubuntu-desktop


This fixed the problem.  I suspect it was some sort of mesa configuration weirdness.

---

### Post by veloce on 2007-10-25
I have the same symptoms (just upgraded to gutsy, intel graphics)

> **ljp37 said:**
> 

  apt-get remove .*mesa.* .*xorg-xserver.*


Is this line correct?  .*xorg-xserver.* gets a "no package found" on my system.

---

### Post by veloce on 2007-10-25
Don't worry, I realised it had to be xserver-xorg!

Cheers - and it has worked for me.  dri is on and randr is working.  

Now to try dual head!

---

### Post by 82_28 on 2007-12-16
Sweet!  Thank you.  That did indeed work.:guitar:

---

### Post by n.l.o on 2008-01-24
hello
I did as stated above. but no DRI:
```
$ glxinfo | grep render
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2

```

As you see below I use the "intel" driver and not the i810.
my xorg.conf:

```
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore" # opengl core module
#	Load		"v4l" #video4linux module
	Load 		"dri" #dri opengl module
#	Load		"dbe" #double buffering
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"swe"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
        Identifier "Intel Graphics Adapter"
        Driver     "intel"
	Option	   "DRI"   "True"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device "Intel Graphics Adapter"
EndSection

```

Is there anything I can do to get DRI: Yes?

 (As usual I have no idea how it affects me to have direct rendering, but it sounds good)
Ceers!

Lenovo ThinkPas z61m with Intel 945 graphics

---

