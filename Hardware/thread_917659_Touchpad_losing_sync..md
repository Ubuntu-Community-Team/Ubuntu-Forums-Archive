---
title: "Touchpad losing sync."
date: 2008-09-12
forum: Hardware
---

### Post by apoth on 2008-09-12
My Dell inspiron 9400 (synaptic?) touchpad frequently stops responding. The following is repeated many times over in dmesg:

> [  150.191042] psmouse.c: issuing reconnect request
[  152.333555] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  152.334531] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  152.335543] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  152.336619] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  152.337245] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1

I've found various suggested fixes around for i8042 kernel options, removing and modprobing the psmouse kernel module, setting the reset value to 0/1 and changing the driver to auto from auto-dev but nothing seems to work.

Does anyone have a fix? I've had the laptop a year and it's only recently started happening, I'm not aware of any kernel or X updates having come down the wire.

Running hardy on 2.6.24-19-generic.

Thanks

---

