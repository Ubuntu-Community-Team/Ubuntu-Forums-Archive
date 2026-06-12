---
title: "Calibrate and rotate input of a TouschScreen"
date: 2010-05-25
forum: Hardware
---

### Post by Robert_Zenz on 2010-05-25
Hello everyone.
I've got a Nexoc S621II (notebook/tablet pc) with a TouchPack Touchscreen. Everything is working fine after I installed a Vanilla Kernel (issue with the touchscreen which is fixed in 2.6.34). My only problem is now that I can't find a way to rotate the input of the touchscreen if I rotate the screen with xrandr.

The modified Synaptics-Driver which is available makes it possible to use the touchpad, but the touchscreen input isn't rotated. Also, it has a little divergence towards the right side, so how can I calibrate it?

Anyone an idea on that one?

[QUOTE=lsusb]Bus 008 Device 002: ID 1bfd:1688 TouchPack Resistive Touch Screen[/QUOTE]

---

### Post by Robert_Zenz on 2010-05-29
I found it!

I'll write a complete How-To later on how to get the whole notebook up and running, for now it's this to get the touchscreen working.

Use this to determine the device:
```
xinput list
```

Calibration:
```

xinput set-prop 12 "Evdev Axis Calibration" 0 4132 0 4135

```

Rotation:
```

#Normal
    xinput set-prop 12 "Evdev Axis Inversion" 0, 0
    xinput set-prop 12 "Evdev Axes Swap" 0

#Right
    xinput set-prop 12 "Evdev Axis Inversion" 1, 0
    xinput set-prop 12 "Evdev Axes Swap" 1

# Inverted
    xinput set-prop 12 "Evdev Axis Inversion" 1, 1
    xinput set-prop 12 "Evdev Axes Swap" 0

# Right
    xinput set-prop 12 "Evdev Axis Inversion" 0, 1
    xinput set-prop 12 "Evdev Axes Swap" 1

```

---

### Post by djhuft on 2011-07-05
Thanks a lot! This helped me get the touchscreen on my Asus All-in-One  PC going. I had looked all over for this. 

One helpful thing for beginners to note is  that in your code the 12 after "set-prop" needs to be changed to  whatever the identifier of your touchscreen happens to be. (You find this when you run xinput list).

---

