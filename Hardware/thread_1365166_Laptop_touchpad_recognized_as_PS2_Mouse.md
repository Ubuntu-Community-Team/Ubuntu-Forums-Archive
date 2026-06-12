---
title: "Laptop touchpad recognized as PS/2 Mouse"
date: 2009-12-26
forum: Hardware
---

### Post by DevgruSeal on 2009-12-26
My Asus P50IJ's touchpad is being recognized as "ImPS/2 Logitech Wheel Mouse", and also lists "Macintosh mouse button emulation".

I don't have a "Touchpad" tab in System>Preferences>Mouse, and I can't use gsynaptics to change touchpad properties. I just want to change the sensitivity of the touchpad tapping, and disable tapping while typing.

I'm new to linux so I don't know where to start troubleshooting/fixing.

Thanks in advance.

---

### Post by taurus on 2009-12-26
I believe gpointing-device-settings replaces gsynaptic so may want to check that out.

---

### Post by DevgruSeal on 2009-12-26
> **taurus said:**
> I believe gpointing-device-settings replaces gsynaptic so may want to check that out.

I gave that one a try just now, but it doesn't offer anything in regards to the touchpad. It only gave me options for middle button and wheel emulation.

---

### Post by taurus on 2009-12-26
I am reading the description and here is what it says.

> 
GUI tool for setting pointing devices. Currently it can configure mouse type
device (mouse, trackpoint etc.) and touchpads.

For mouse you can configure middle button emulation, wheel emulation and
scrolling.

It can enable and disable touchpad, or srolling on it as well as additional
parameters like palm detection, locked drags, tapping and scrolling.


---

### Post by DevgruSeal on 2009-12-26
> **taurus said:**
> I am reading the description and here is what it says.

Yeah, but that's the problem I'm trying to resolve: The utilities to configure touchpads do not recognize it as an actual touchpad, so they give me options for a PS/2 device.

---

### Post by jonest1 on 2009-12-26
I just bought an HP mini 311 and I am seeing the exact same behavior as you.

In the end, I found the touchpad is not a synaptics touchpad, but an Alps.  The support for Alps in Linux is spotty at best.  It works, but is not configurable.

Search in the forums and you will find a lot of threads as the Alps is becoming more popular.

---

