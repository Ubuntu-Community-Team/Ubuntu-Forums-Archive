---
title: "&quot;Locking drags&quot; and other touchpad controls: possible?"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by SomeGuyDude on 2007-11-05
I've been looking around, did a whole slew of Google searches, and all I could find on this was a manual for the ability to change tap zones, but that's not what I need here.

When I ported over, the first thing I noticed is that I really, really took advantage of the Synaptics touchpad controls. I had a lot of tap zones and I would really love to be able to do locking drags, where you tap-tap/hold to start the drag, then you can let go all you want and the drag holds, another tap to "release". I hate doing the two-handed deal with the actual pad buttons.

Is this possible with Ubuntu? I saw Gsynaptics, but it didn't have that option.

---

### Post by SomeGuyDude on 2007-11-07
Up we go. Any word on this?

---

### Post by sistoviejo on 2007-11-11
I don't know if locking drags are possible. I am also interested in enabling this.
You can change tocuhpad configuration on the X.org config file.
Read here: [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

---

### Post by sistoviejo on 2007-12-07
bump!

Anyone seen anything on how to enable locking drags?
I also am interested in using this feature.

---

### Post by rsotam on 2008-02-04
Hi,

You can add and set the option "LockedDrags".
This is my section "InputDevice":

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
Option "SHMConfig" "on"
Option "LockedDrags" "on"
EndSection

Good luck!

---

### Post by sistoviejo on 2008-02-09
Thank you. 
I would love to try it to see if it works but now I have removed Ubuntu from the partition.
I use it in a virtual machine now in my laptop because my hardware is mostly unsupported natively.
Did this work for anybody else?

UPDATE: It works.

---

