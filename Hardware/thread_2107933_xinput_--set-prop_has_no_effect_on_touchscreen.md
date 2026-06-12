---
title: "xinput --set-prop has no effect on touchscreen"
date: 2013-01-23
forum: Hardware
---

### Post by wasu on 2013-01-23
Hi,

I am using the following 2 touchscreens: DELL ST2220T, Samsung LTI220MT02. I have just installed Ubuntu 12.10 because I have read that 12.10 has better touchscreen support than 12.04.

Both touchsreens work, but for both touchscreens the touch inputs are interpreted for both axes in the contrary direction:
When I move right with the finger, the mouse pointer moves left and the other way round.
When I move up with the finger, the mouse pointer moves down and the other way round.

So I have tried the following (example with DELL monitor):
```

root@wasumobile2:/home/walter# xinput --list
&#9121;Virtual core pointer                id=2   [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer     id=4   [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad     id=11  [slave  pointer  (2)]
&#9116;   &#8627; LG Display LGD-MultiTouch      id=16  [slave  pointer  (2)]
&#9123;Virtual core keyboard               id=3   [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard    id=5   [slave  keyboard (3)]
...

```The DELL touchsreen is displayed as "LG Display LGD-MultiTouch". I get details of the configuration with:
```

root@wasumobile2:/home/walter# xinput --list-props 16
Device 'LG Display LGD-MultiTouch':
        Device Enabled (132):   1
        Coordinate Transformation Matrix (134): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (256):     0
        Device Accel Constant Deceleration (257):       1.000000
        Device Accel Adaptive Deceleration (258):       1.000000
        Device Accel Velocity Scaling (259):    10.000000
        Device Product ID (251):        8146, 100
        Device Node (252):      "/dev/input/event15"
        Evdev Axis Inversion (574):     0, 0
        Evdev Axis Calibration (575):   <no items>
        Evdev Axes Swap (576):  0
        Axis Labels (577):      "Abs MT Position X" (558), "Abs MT Position Y" (559), "None" (0), "None" (0)
        Button Labels (578):    "Button Unknown" (566), "Button Unknown" (566), "Button Unknown" (566), "Button Wheel Up" (138), "Button Wheel Down" (139)
        Evdev Middle Button Emulation (579):    0
        Evdev Middle Button Timeout (580):      50
        Evdev Third Button Emulation (581):     0
        Evdev Third Button Emulation Timeout (582):     1000
        Evdev Third Button Emulation Button (583):      3
        Evdev Third Button Emulation Threshold (584):   20
        Evdev Wheel Emulation (585):    0
        Evdev Wheel Emulation Axes (586):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (587):    10
        Evdev Wheel Emulation Timeout (588):    200
        Evdev Wheel Emulation Button (589):     4
        Evdev Drag Lock Buttons (590):  0

```Now I try to invert the axes:

```
root@wasumobile2:/home/walter# xinput --set-prop 16 574 1 1

```I know check if the values have been saved.

```

root@wasumobile2:/home/walter# xinput --list-props 16
Device 'LG Display LGD-MultiTouch':
        Device Enabled (132):   1
        Coordinate Transformation Matrix (134): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        Device Accel Profile (256):     0
        Device Accel Constant Deceleration (257):       1.000000
        Device Accel Adaptive Deceleration (258):       1.000000
        Device Accel Velocity Scaling (259):    10.000000
        Device Product ID (251):        8146, 100
        Device Node (252):      "/dev/input/event15"
        Evdev Axis Inversion (574):     1, 1
        Evdev Axis Calibration (575):   <no items>
        Evdev Axes Swap (576):  0
        Axis Labels (577):      "Abs MT Position X" (558), "Abs MT Position Y" (559), "None" (0), "None" (0)
        Button Labels (578):    "Button Unknown" (566), "Button Unknown" (566), "Button Unknown" (566), "Button Wheel Up" (138), "Button Wheel Down" (139)
        Evdev Middle Button Emulation (579):    0
        Evdev Middle Button Timeout (580):      50
        Evdev Third Button Emulation (581):     0
        Evdev Third Button Emulation Timeout (582):     1000
        Evdev Third Button Emulation Button (583):      3
        Evdev Third Button Emulation Threshold (584):   20
        Evdev Wheel Emulation (585):    0
        Evdev Wheel Emulation Axes (586):       0, 0, 4, 5
        Evdev Wheel Emulation Inertia (587):    10
        Evdev Wheel Emulation Timeout (588):    200
        Evdev Wheel Emulation Button (589):     4
        Evdev Drag Lock Buttons (590):  0

```They were saved, I can see this in the following line:
```
Evdev Axis Inversion (574):    1, 1

```However this has no effect on the touch-inputs, no change, same as described at the beginning.

I have tried to invert the axis with input --set-prop on a Logitech Mouse, it worked after executing the command. So I do not understand, why the axis are not inverted by the xinput --set-prop command for the touchscreen.

Please help.

Regards

---

