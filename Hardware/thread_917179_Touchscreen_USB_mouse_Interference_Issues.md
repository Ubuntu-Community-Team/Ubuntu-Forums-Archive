---
title: "Touchscreen USB mouse Interference Issues"
date: 2008-09-11
forum: Hardware
---

### Post by asc2null on 2008-09-11
I have a tx1000 hp laptop which uses a egalax touchscreen.  I'm using the Touchkit_64 drivers and they work great.
The only problem is this, to use a usb mouse the touchscreen and the usb mouse can't both have corepointer on it.
When I remove corepointer from EETI or Mouse0 both will work.  Except that when I actually follow the point of the touchscreen a click will "drag" the mouse through each intermediate pixel while clicking to the new point.

Meaning that in GIMP while drawing if I have the pointer at one corner and tap the other corner it will drawer a diagonal line instead of a dot.  This is annoying.

Is anyone using a touchscreen and usb/ps/2 mouse with this problem solved?

I have also tried sendcoreevents which didn't work either.

---

### Post by hybridgeek on 2008-10-28
asc2null,
I'm having a similar problem.  I got the touchscreen drivers in place and working, but they only work perfectly if I use the CorePointer directive on the Touchscreen.  If I have it on the mouse (default), then it causes artifacts when trying to use it and generally fails to work.  If I use CorePointer on the device, it works fine, but then my USB mouse fails to work.  The touchpad still works fine.  I found a suggestion to use ServerFlags as a section in xorg.conf and use the command "Option 'AllowEmptyInput'", but that resulted in my keyboard not working.  So... end result is, I have no solution yet, but I wanted to let you know you're not the only one.  Hopefully some guru will catch onto this thread and have a solution for us.

---

