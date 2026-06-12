---
title: "New two finger scroll settings for acer aspire timeline 1810tz on lucid?"
date: 2010-06-11
forum: Hardware
---

### Post by mrsi on 2010-06-11
Until recently the following worked for getting two finger scrolling working my acer aspire timeline 1810tz on lucid:

```
synclient EmulateTwoFingerMinW=7
synclient EmulateTwoFingerMinZ=20
synclient VertTwoFingerScroll=1
```

This worked fine for a while on lucid, and then it broke.

I read about some changes (with xorg I think), and that I need to use xinput now to set the properties. So I refered to the synaptics man page, and came up with this:

```
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 7
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 20
xinput --set-prop --type=int --format=8 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0
```

...but that doesn't work either.

Can someone tell me what I am doing wrong?

---

### Post by eken on 2010-10-16
Two-finger scroll ACER 1810TZ.

Step 1:
Create a file, the location depends on the Ubuntu version.
Use a terminal or Alt-F2,
Ubuntu 10.04 -> gksudo gedit /usr/lib/X11/xorg.conf.d/96-synaptics-twofing.conf
Ubuntu 10.10 -> gksudo gedit /usr/share/X11/xorg.conf.d/96-synaptics-twofing.conf
Copy and paste this in the file:```
Section "InputClass"
Identifier "touchpad two finger scrolling"
MatchIsTouchpad "on"
MatchDevicePath "/dev/input/event*"
Option "HorizScrollDelta" "0"
Option "MinSpeed" "0.5"
Option "MaxSpeed" "0.5"
#Option "AccelFactor" "0.0010"
Option "EmulateTwoFingerMinZ" "40"
Option "EmulateTwoFingerMinW" "11"
Option "VertTwoFingerScroll" "True"
Option "HorizTwoFingerScroll" "True"
Option "VertEdgeScroll" "False"
Option "HorizEdgeScroll" "False"
Option "JumpyCursorThreshold" "250"
Driver "synaptics"
EndSection
```Save the file.

Step 2:
Now press Alt+F2 again and enter
gconftool-2 --set /desktop/gnome/peripherals/touchpad/scroll_method --type=int 2
Nothing will happen then, that's okay. Log off and back in, now two-finger scrolling on the touchpad should work. :guitar:

---

### Post by yetiARC on 2010-11-28
Works just fine under Maverick, as long as it's run as a live session from  DVD.
After a full install on HD the method didn't work anymore. When I try to two finger scroll, the cursor just jumps around.
Any ideas?
Thx
yeti

---

### Post by ludwigbaum on 2011-02-25
Sorry, I am late ...
The script works fine, best solution ever seen for the touchpad.
It works in full installation on HD.
The last line (step 2) has to be done as user, not root.

---

### Post by yetiARC on 2011-02-25
Allright. 2finger scroll works nicely. Thanks!
One little quirk still. The gnome configuration editor offers the touchpad option "disable while typing". Has no effect, though.
Anybody else having this "problem" ... or a solution to it??

---

