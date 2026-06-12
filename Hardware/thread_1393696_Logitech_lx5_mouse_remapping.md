---
title: "Logitech lx5 mouse remapping"
date: 2010-01-29
forum: Hardware
---

### Post by billyboy1995 on 2010-01-29
I have the logitech lx5 mouse and i was wondering if i could get ubuntu 9.10 to recognise and remap the side scrolling buttons to be a back and forwards buttons.

Thanks

---

### Post by billyboy1995 on 2010-01-29
anyone? Help would be nice. Anything that might help would help.

---

### Post by tilator on 2011-04-26
With Ubuntu 10.10 this could be done by editing xorg.conf:

Before:

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

After:

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5 7 6"
EndSection

---

