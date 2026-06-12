---
title: "Logitech G7 Back Button (side)"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by measekite on 2007-09-26
I have read all of the posts regarding this.

It does not work.  After following the instructions twice gnome will not boot due to a protocol error in endev as much as I can tell.  I had to boot to recovery and restore my backed up xorg.conf.bak file.

I went to synaptic and xserver-xorg-input-evdev is installed.

I then edited xorg.conf as follows:
**Section** "InputDevice"
**Identifier** "Configured Mouse"
**Driver** "evdev"
**Option** "Name" "Logitech USB Gaming Mouse"
**Option** "CorePointer"
# Option "Device" "/dev/input/mice"
# Option "Protocol" "ImPS/2"
**Option** "ZAxisMapping" "4 5 6 7 8"
**Option** "Emulate3Buttons" "true"

Do not know what to do.  I think that the problem is evdev but other than checking it for installation I do not know what to do.

[COLOR=SeaGreen]**Anybody have any ideas?**[/COLOR]

---

