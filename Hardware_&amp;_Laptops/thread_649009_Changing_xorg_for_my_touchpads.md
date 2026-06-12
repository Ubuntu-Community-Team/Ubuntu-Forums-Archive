---
title: "Changing xorg for my touchpads"
date: 2007-12-24
forum: Hardware &amp; Laptops
---

### Post by spinstartshere on 2007-12-24
Looking at my xorg.conf file yesterday, I noticed this:
```
Section "InputDevice" 
    Identifier    "Configured Mouse" 
    Driver        "mouse" 
    Option        "CorePointer" 
    Option        "Device"        "/dev/input/mice" 
    Option        "Protocol"        "ImPS/2" 
    Option        "ZAxisMapping"        "4 5" 
    Option        "Emulate3Buttons"    "true" 
EndSection 
 
Section "InputDevice" 
    Identifier    "Synaptics Touchpad" 
    Driver        "synaptics" 
    Option        "SendCoreEvents"    "true" 
    Option        "Device"        "/dev/psaux" 
    Option        "Protocol"        "auto-dev" 
    Option        "HorizEdgeScroll"    "1" 
    Option        "HorizScrollDelta"    "1" 
    Option        "SHMConfig"        "true" 
EndSection
```The Synaptics Touchpad, I found out yesterday, is the multimedia keys of my laptop, and I'm assuming the Configured Mouse is the touchpad I'm using to control my laptop.  Is there a way of modifying the file in such a way that the touchpad is recognised as a touchpad so that I can use it properly?

---

### Post by nick_h on 2007-12-24
The "Configured Mouse" section will be for an external mouse.
The "Synaptics Touchpad" section will be for your touchpad.

> The Synaptics Touchpad, I found out yesterday, is the multimedia keys of my laptop
I'm not quite sure what you mean by this.

> so that I can use it properly?
What is the problem that you have with your touchpad?

---

### Post by spinstartshere on 2007-12-24
There's no external mouse connected to the computer, so unless "Configured Mouse" means something other than that, I'm pretty sure it's the touchpad it's referring to.  The multimedia keys on my laptop -- Play, Pause, etc. -- are touch-sensitive keys, ie. a second touchpad.  The touchpad that controls the cursor only moves the cursor.  Horizontal and vertical scrolling are not possible.

---

