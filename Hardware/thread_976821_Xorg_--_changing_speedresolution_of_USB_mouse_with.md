---
title: "Xorg -- changing speed/resolution of USB mouse without affecting trackpad"
date: 2008-11-09
forum: Hardware
---

### Post by philpem on 2008-11-09
Hi,
I'm using Kubuntu 8.04 LTS on an Asus Eee 1000H. This machine has an Elantech trackpad, which appears as /dev/input/mouse1. For the most part, X works fine (with the possible exception of a couple of graphics issues caused by the Intel driver).

I wanted to add an external USB mouse to the laptop, so I bought a Genius Netscroll 100 from a local computer shop. This is a fairly standard 800dpi optical mouse with a USB interface.

The issue is, the cursor moves across the screen far too quickly. By that I mean a quarter-inch movement of the mouse is enough to send the cursor flying from one side of the screen to the other. Hardly ideal. So I added this line to the "Configured Mouse" InputDevice section in xorg.conf:
```
Option "Sensitivity" "0.25"
```

This slows the USB mouse down fine, but also slows the trackpad down to the point of being almost unusable - that now takes three complete left-to-right 'swipes' across the pad to move the cursor across the screen.

I've also tried adding another InputDevice section --
```

Section "InputDevice"
	Identifier	"USBMouse"
	Driver		"mouse"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/mouse2"
	Option		"Sensitivity"	"0.25"
EndSection

```
And amended the Configured Mouse section as follows:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Device"		"/dev/input/mouse1"
	Option		"CorePointer"
EndSection

```

This works great -- as long as the USB mouse is plugged in when X is started. I can tell that having to restart X every time I hibernate the laptop is going to get very annoying very quickly.

I also tried the same thing, but with Configured Mouse set to use /dev/input/mice instead -- this caused X to double up mouse events, turning my clicks into double-clicks.

Does anyone know if it's possible to set the sensitivity for my USB mouse (or just USB mice in general) separately to that for the trackpad, without mangling mouse events or killing off hotplug for my USB mouse?

Thanks,
Phil.

---

### Post by wgrant on 2008-11-09
You can use the 'xinput' command line tool to change these things while X is running. You probably want to use 'xinput set-ptr-feedback', but the manpage describes things well.

We're looking at producing a GUI for this and other input stuff for Ubuntu 9.04.

---

### Post by philpem on 2008-11-10
> **wgrant said:**
> You can use the 'xinput' command line tool to change these things while X is running. You probably want to use 'xinput set-ptr-feedback', but the manpage describes things well.

Indeed it does.. Interestingly, 'xinput get-feedbacks "Configured Mouse"' reports:
```

1 feedback class
PtrFeedbackClass id=0
        accelNum is 10
        accelDenom is 20
        threshold is 2

```
If I then run:
```
xinput set-ptr-feedback "Configured Mouse" 2 10 20
```
The trackpad slows down to around half its usual speed, and the mouse goes from "too fast" to "almost sane".

At the moment, I'm using ```
xinput set-ptr-feedback "Configured Mouse" 2 20 20
``` for the trackpad, and ```
xinput set-ptr-feedback "Configured Mouse" 2 10 20
``` for when I'm using the USB mouse.

There doesn't seem to be a way to set Xorg up to have one InputDevice for the USB mouse and one for the trackpad, though (well, not without sacrificing hotplug) -- unless anyone knows otherwise?

> **wgrant said:**
> We're looking at producing a GUI for this and other input stuff for Ubuntu 9.04.

Sounds good :):)

Thanks,
Phil.

---

