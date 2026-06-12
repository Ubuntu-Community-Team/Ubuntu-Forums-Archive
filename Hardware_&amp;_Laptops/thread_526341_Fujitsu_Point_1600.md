---
title: "Fujitsu Point 1600"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by yosef on 2007-08-15
Does anyone know what the specs are on the graphics card and monitor for a fujitsu point 1600?

I searched forever and this is all I got:

svga dstn color lcd
backlit 10.4" (264mm) diagonal
0.26mm dot pitch
800x600 svga resolution up to 65536 colors

but I cant get x up and running with only that... or can I?  Any suggestions?

---

### Post by yosef on 2007-08-15
well, the desktop seems to be ok after using: Xorg -configure

But the resistive touchscreen is not responding.

xorg.conf has this to say on the subject:

Section "InputDevice"
           Identifier  "Mouse0"
           Driver  "mouse"
           Option  "Protocol" "auto"
           Option  "Device" "/dev/input/mice"
           Option  "ZAxisMapping" "4 5 6 7"
EndSection

Any ideas?  I have no clue what to put!

---

### Post by yosef on 2007-08-15
What about the wacom driver?  Would that help for this tablet?  How do I enter it in the xorg.conf?

---

### Post by yosef on 2007-08-19
Is there any way to wrap the pen driver for either win98 or win95?  Any way to use it at all?

---

