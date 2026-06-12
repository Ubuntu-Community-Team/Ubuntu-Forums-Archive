---
title: "Toughbook CF-29 touchscreen disabled"
date: 2016-07-28
forum: Hardware
---

### Post by jvglynnjr on 2016-07-28
```
xinput --list
``` shows:

```
LBPS/2 Fujitsu Lifebook TouchScreen         id=13    [slave  pointer  (2)]
```

```
xinput --enable "LBPS/2 Fujitsu Lifebook TouchScreen"

```
appears to have no effect.  

```
xinput list-props "LBPS/2 Fujitsu Lifebook TouchScreen"
``` gives

```

Device 'LBPS/2 Fujitsu Lifebook TouchScreen':
    Device Enabled (116):    1
    Coordinate Transformation Matrix (118):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (245):    0
    Device Accel Constant Deceleration (246):    1.000000
    Device Accel Adaptive Deceleration (247):    1.000000
    Device Accel Velocity Scaling (248):    10.000000
    Device Product ID (234):    2, 9
    Device Node (235):    "/dev/input/event7"
    Evdev Axis Inversion (249):    0, 0
    Evdev Axis Calibration (250):    <no items>
    Evdev Axes Swap (251):    0
    Axis Labels (252):    "Abs X" (268), "Abs Y" (269)
    Button Labels (253):    "Button Unknown" (237), "Button Unknown" (237), "Button Unknown" (237), "Button Wheel Up" (122), "Button Wheel Down" (123)
    Evdev Scrolling Distance (254):    0, 0, 0
    Evdev Middle Button Emulation (255):    0
    Evdev Middle Button Timeout (256):    50
    Evdev Third Button Emulation (257):    0
    Evdev Third Button Emulation Timeout (258):    1000
    Evdev Third Button Emulation Button (259):    3
    Evdev Third Button Emulation Threshold (260):    20
    Evdev Wheel Emulation (261):    0
    Evdev Wheel Emulation Axes (262):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (263):    10
    Evdev Wheel Emulation Timeout (264):    200
    Evdev Wheel Emulation Button (265):    4
    Evdev Drag Lock Buttons (266):    0




```
Is there a simple way to rule out that this is just defective hardware?  Running Lubuntu 16.04 and I don't have another OS available.

---

