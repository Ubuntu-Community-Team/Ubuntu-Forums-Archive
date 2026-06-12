---
title: "using Panasonic Tough Book??"
date: 2009-05-05
forum: Hardware
---

### Post by oldsoundguy on 2009-05-05
Has anyone besides the US Military been able to convert the Panasonic Tough book to any form of Linux and get it to work out of the box?

I know that the military buys them and dumps Windows the moment the seal is broken and installs their own version of Unix/Linux on them.  (nothing worse than the bsod in the middle of a firefight!)
(but MS still carries the OS in their "usage" and "sales" stats!!)

---

### Post by oldsoundguy on 2009-05-06
bump

---

### Post by acidd_uk on 2009-05-19
We use them at my work - though not with Ubuntu. We used the CF-18 a few years ago and more recently used the CF-19 Mk2 with Red Hat 5.3. However, the CF-19 Mk2 has no Linux drivers for the screen brightness controls.

The CF-19 Mk3 should be out soon - hopefully it will feature improved Linux support...

---

### Post by acidd_uk on 2009-05-22
Ok, I have got my hands on a CF-19 Mk3. Using the Jaunty live CD, the brightness controls work nicely (the do also on Redhat EL 5.3) without any modifications needed.

The touchscreen however needs some work. By deafult, it's detected by Xorg as "Fujitsu Component USB Touch Panel" on /dev/input/event5. However, it defaults to relative mode, rather than absolute, so you can drag the pointer by starting anywhere on the screen, the pointer moves in sync with the drag, but does not initally move to the start point of the drag.

Possibly as a side effect of this, you cannot cause a click event by tapping the screen with the pointer.

I have the device on loan until Tuesday, will report back if I make any progress with absolute mode and clicking.

---

### Post by acidd_uk on 2009-05-26
Ok, the touch screen actually works in absolute mode, as long as you set the touchscreen mode to 'touchscreen' in the BIOS (as opposed to 'tablet'). Now I need to work out how to calibrate it - there is no entry for it in the xorg.conf, so I need to work out how xorg is driving it and how to pass the equivalent of the Xmin, Xmas etc parameters to that driver, as per the InputDevice section described here:

[http://www.groomlakelabs.com/?q=linux_input_usb_touchscreen_howto](http://www.groomlakelabs.com/?q=linux_input_usb_touchscreen_howto)

I'll raise a new thread in a more appropriate subforum and link back here...

Edit: Touchscreen (auto) setup thread:
[http://ubuntuforums.org/showthread.php?t=1170449](http://ubuntuforums.org/showthread.php?t=1170449)

---

