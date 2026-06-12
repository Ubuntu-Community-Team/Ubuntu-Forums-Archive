---
title: "How to get my touchscreen's special controls working."
date: 2012-01-10
forum: Hardware
---

### Post by roelforg on 2012-01-10
Hello,

I've got a medion MD20165 20" touch screen.
I've installed Ubuntu Server 11.10 on my pc,
also i've installed xdm and lxde.
It's nice and light,
i'm using an old pc with a pIII and 256 mb ram.
Thanks to the combi of the lightweight ubuntu and the light lxde, it's works nice and fast!
If i use Standard Ubuntu it's slower than sirup.
(Takes 5 min to boot, 2 min for unity (of gnome) to respond to anything (i suspect because they fill my mem causing heave swap usage)).
With this setup it works nice and fast. (boot times are under 2 min, response almost direct, 2-3 ms time but that's okay)
Anyway...
My touchscreen worked directly (i plugged in the usb and touched the screen and the mouse went directly to my finger!)
But when connected to windows (different pc...) i can also scroll by swiping my finger up or down.
Also if i held my finger (or stylus) on the screen for 5 secs it did a right click.
These are the 2 things i'm really missing...
Everything else is working fine.
I didn't have to do any calibration (never did, the factory did that for me, saves me a headache!)
I only had to do an automatic adjustment (the screen was offset to the right and top).

How can i fix this?

xinput list-props output:
```

Device 'Quanta Computer Inc. Optical Touch Screen':
    Device Enabled (118):    1
    Coordinate Transformation Matrix (120):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (238):    0
    Device Accel Constant Deceleration (239):    1.000000
    Device Accel Adaptive Deceleration (240):    1.000000
    Device Accel Velocity Scaling (241):    10.000000
    Evdev Axis Inversion (242):    0, 0
    Evdev Axis Calibration (243):    <no items>
    Evdev Axes Swap (244):    0
    Axis Labels (245):    "Abs X" (255), "Abs Y" (256)
    Button Labels (246):    "Button Unknown" (235), "Button Unknown" (235), "Button Unknown" (235), "Button Wheel Up" (124), "Button Wheel Down" (125)
    Evdev Middle Button Emulation (247):    0
    Evdev Middle Button Timeout (248):    50
    Evdev Wheel Emulation (249):    0
    Evdev Wheel Emulation Axes (250):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (251):    10
    Evdev Wheel Emulation Timeout (252):    200
    Evdev Wheel Emulation Button (253):    4
    Evdev Drag Lock Buttons (254):    0

```

If i can get this working, i'll have a great pc.

---

### Post by roelforg on 2012-01-13
Never mind,
fixed it....
Used ginn and xbindkeys.
Bound a comby of unpressable keys to xdotool and made ginn press it.

---

