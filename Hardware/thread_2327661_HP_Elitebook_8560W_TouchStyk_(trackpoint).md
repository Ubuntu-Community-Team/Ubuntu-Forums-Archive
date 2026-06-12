---
title: "HP Elitebook 8560W TouchStyk (trackpoint)"
date: 2016-06-13
forum: Hardware
---

### Post by salocharger on 2016-06-13
Issue: the touchstyk (trackpoint) is missing one neat feature: tap-to-click. In Windows it works just fine so I know the sensor to detect tapping on trackpoint is there somewhere.
I think the problem is that it is somehow wrongly detected as a generic PS/2 mouse (see below for output of 'xinput --list').
Moving the cursor works like a charm. Only tap-to-click is not working. I tried playing around with the properties of devices 11 (PS/2 mouse) and 12 (Synaptics Touchpad) but no luck so far...

Been digging the past few days about this issue but to no avail so coming here hoping for a solution. Thanks in advance.

```
 xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; HP HD Webcam [Fixed]                        id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=13    [slave  keyboard (3)]
```

```
xinput -list-props 11
Device 'PS/2 Generic Mouse':
    Device Enabled (141):    1
    Coordinate Transformation Matrix (143):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (265):    0
    Device Accel Constant Deceleration (266):    1.000000
    Device Accel Adaptive Deceleration (267):    1.000000
    Device Accel Velocity Scaling (268):    10.000000
    Device Product ID (261):    2, 1
    Device Node (262):    "/dev/input/event5"
    Evdev Axis Inversion (269):    0, 0
    Evdev Axes Swap (271):    0
    Axis Labels (272):    "Rel X" (151), "Rel Y" (152)
    Button Labels (273):    "Button Left" (144), "Button Middle" (145), "Button Right" (146), "Button Wheel Up" (147), "Button Wheel Down" (148)
    Evdev Scrolling Distance (274):    0, 0, 0
    Evdev Middle Button Emulation (275):    0
    Evdev Middle Button Timeout (276):    50
    Evdev Third Button Emulation (277):    0
    Evdev Third Button Emulation Timeout (278):    1000
    Evdev Third Button Emulation Button (279):    3
    Evdev Third Button Emulation Threshold (280):    20
    Evdev Wheel Emulation (281):    0
    Evdev Wheel Emulation Axes (282):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (283):    10
    Evdev Wheel Emulation Timeout (284):    200
    Evdev Wheel Emulation Button (285):    4
    Evdev Drag Lock Buttons (286):    0
```

```
xinput -list-props 12
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (141):    1
    Coordinate Transformation Matrix (143):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (265):    1
    Device Accel Constant Deceleration (266):    2.500000
    Device Accel Adaptive Deceleration (267):    1.000000
    Device Accel Velocity Scaling (268):    12.500000
    Synaptics Edges (289):    1767, 5397, 1649, 4615
    Synaptics Finger (290):    25, 30, 0
    Synaptics Tap Time (291):    180
    Synaptics Tap Move (292):    239
    Synaptics Tap Durations (293):    180, 100, 100
    Synaptics ClickPad (294):    0
    Synaptics Middle Button Timeout (295):    75
    Synaptics Two-Finger Pressure (296):    282
    Synaptics Two-Finger Width (297):    7
    Synaptics Scrolling Distance (298):    108, 108
    Synaptics Edge Scrolling (299):    0, 0, 0
    Synaptics Two-Finger Scrolling (300):    1, 1
    Synaptics Move Speed (301):    1.000000, 1.750000, 0.036704, 0.000000
    Synaptics Off (302):    2
    Synaptics Locked Drags (303):    0
    Synaptics Locked Drags Timeout (304):    5000
    Synaptics Tap Action (305):    2, 3, 0, 0, 1, 3, 2
    Synaptics Click Action (306):    1, 1, 0
    Synaptics Circular Scrolling (307):    0
    Synaptics Circular Scrolling Distance (308):    0.100000
    Synaptics Circular Scrolling Trigger (309):    0
    Synaptics Circular Pad (310):    0
    Synaptics Palm Detection (311):    0
    Synaptics Palm Dimensions (312):    10, 200
    Synaptics Coasting Speed (313):    20.000000, 50.000000
    Synaptics Pressure Motion (314):    30, 160
    Synaptics Pressure Motion Factor (315):    1.000000, 1.000000
    Synaptics Resolution Detect (316):    1
    Synaptics Grab Event Device (317):    0
    Synaptics Gestures (318):    1
    Synaptics Capabilities (319):    1, 1, 1, 1, 1, 1, 1
    Synaptics Pad Resolution (320):    81, 40
    Synaptics Area (321):    0, 0, 0, 0
    Synaptics Noise Cancellation (322):    8, 8
    Device Product ID (261):    2, 7
    Device Node (262):    "/dev/input/event6"
```

---

### Post by ochoadavid on 2017-02-17
I'm missing this specific feature too. +1

---

### Post by zeller-michael on 2017-12-26
I'm missing also this feature. so +1
(and I'm looking for a way to change the TrackPoint's sensitivity)

My HW (HP Elitebook 8570w) list looks like:
```

-8570w:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer:13                         id=6    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-relative-pointer:13                id=7    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; xwayland-keyboard:13                        id=8    [slave  keyboard (3)]
8570w:~$ xinput -list-props 4
Device 'Virtual core XTEST pointer':
    Device Enabled (119):    1
    Coordinate Transformation Matrix (121):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    XTEST Device (238):    1
8570w:~$ xinput -list-props 6
Device 'xwayland-pointer:13':
    Device Enabled (119):    1
    Coordinate Transformation Matrix (121):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (244):    0
    Device Accel Constant Deceleration (245):    1.000000
    Device Accel Adaptive Deceleration (246):    1.000000
    Device Accel Velocity Scaling (247):    10.000000
```

Any ideas?

---

### Post by JamesTheAwesomeDude on 2018-06-23
Alas, far from being a "dead thread", this issue is still alive and well. (EliteBook 8470p here, on both Debian 9.4 and Ubuntu 18.04)

Sadly, the "Tapping" option that works for libinput touchpad does not work for libinput pointer...and XFCE's settings got nothing.

The problem is that it's being recognized AS a "PS/2 Generic Mouse"

---

