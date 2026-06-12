---
title: "Corsair Raptor M4 Mouse switching DPI when moved"
date: 2013-12-17
forum: Hardware
---

### Post by KryoMouse on 2013-12-17
Treated myself to a new mouse for my overly large hands owing to my other one giving up the ghost entirely. However, when I move it the DPI switches of its own accord! No event other than cursor movement is being detected when I test through xinput, and pressing the DPI button yields the same result; no detected events, but the DPI switches up.

I've never had to mess with the xorg.conf too much for mice, but here's the terminal output for the device.

```
skrikey@mausbox:~$ xinput list-props 14
Device 'SONiX USB Device':
        Device Enabled (141):   1
        Coordinate Transformation Matrix (143): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (493):     0
        Device Accel Constant Deceleration (494):       1.000000
        Device Accel Adaptive Deceleration (495):       1.000000
        Device Accel Velocity Scaling (496):    10.000000
        Device Product ID (259):        3141, 33537
        Device Node (260):      "/dev/input/event20"
        Evdev Axis Inversion (497):     0, 0
        Evdev Axes Swap (499):  0
        Axis Labels (500):      "Rel X" (151), "Rel Y" (152), "Rel Vert Wheel" (504)
        Button Labels (501):    "Button Left" (144), "Button Middle" (145), "Button Right" (146), "Button Wheel Up" (147), "Button Wheel Down" (148), "Button Horiz Wheel Left" (149), "Button Horiz Wheel Right" (150), "Button Side" (502), "Button Extra" (503), "Button Unknown" (477), "Button Unknown" (477), "Button Unknown" (477), "Button Unknown" (477)
        Evdev Middle Button Emulation (479):    0
        Evdev Middle Button Timeout (480):      50
        Evdev Third Button Emulation (481):     0
        Evdev Third Button Emulation Timeout (482):     1000
        Evdev Third Button Emulation Button (483):      3
        Evdev Third Button Emulation Threshold (484):   20
        Evdev Wheel Emulation (485):    0
        Evdev Wheel Emulation Axes (486):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (487):    10
        Evdev Wheel Emulation Timeout (488):    200
        Evdev Wheel Emulation Button (489):     4
        Evdev Drag Lock Buttons (490):  0

```

Any help that could be offered would be gratefully received.

---

