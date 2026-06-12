---
title: "T303UA stylus button problems"
date: 2017-04-12
forum: Hardware
---

### Post by magnesus2 on 2017-04-12
I'm trying to make my T303UA fully functional under Ubuntu. Almost everything works but I have problem with missing stylus button. 

xinput report:

```

Device 'ELAN22A5:00 04F3:22A5 Pen':
    Device Enabled (140):    1
    Coordinate Transformation Matrix (142):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (274):    0
    Device Accel Constant Deceleration (275):    1.000000
    Device Accel Adaptive Deceleration (276):    1.000000
    Device Accel Velocity Scaling (277):    10.000000
    Device Product ID (266):    1267, 8869
    Device Node (265):    "/dev/input/event19"
    Evdev Axis Inversion (306):    0, 0
    Evdev Axis Calibration (307):    <no items>
    Evdev Axes Swap (308):    0
    Axis Labels (309):    "Abs X" (299), "Abs Y" (300), "Abs Pressure" (305)
    Button Labels (310):    "Button 0" (304), "Button Unknown" (303), "Button Unknown" (303), "Button Wheel Up" (146), "Button Wheel Down" (147)
    Evdev Scrolling Distance (311):    0, 0, 0
    Evdev Middle Button Emulation (312):    0
    Evdev Middle Button Timeout (313):    50
    Evdev Third Button Emulation (314):    0
    Evdev Third Button Emulation Timeout (315):    1000
    Evdev Third Button Emulation Button (316):    3
    Evdev Third Button Emulation Threshold (317):    20
    Evdev Wheel Emulation (318):    0
    Evdev Wheel Emulation Axes (319):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (320):    10
    Evdev Wheel Emulation Timeout (321):    200
    Evdev Wheel Emulation Button (322):    4
    Evdev Drag Lock Buttons (323):    0

```

One of the stylus buttons works as middle click, which is ok, but the second one doesn't work - xev doesn't report it, it shows up in evtest though as BTN_TOOL_PEN:

```

ent: time 1492004466.432449, type 3 (EV_ABS), code 0 (ABS_X), value 12600
Event: time 1492004466.432449, type 3 (EV_ABS), code 1 (ABS_Y), value 7992
Event: time 1492004466.432449, -------------- SYN_REPORT ------------
Event: time 1492004466.713275, type 1 (EV_KEY), code 320 (BTN_TOOL_PEN), value 0
Event: time 1492004466.713275, -------------- SYN_REPORT ------------
Event: time 1492004466.717712, type 1 (EV_KEY), code 320 (BTN_TOOL_PEN), value 1
Event: time 1492004466.717712, -------------- SYN_REPORT ------------
Event: time 1492004466.728014, type 1 (EV_KEY), code 321 (BTN_TOOL_RUBBER), value 1
Event: time 1492004466.728014, -------------- SYN_REPORT ------------
Event: time 1492004467.303023, type 3 (EV_ABS), code 0 (ABS_X), value 12588
Event: time 1492004467.303023, type 3 (EV_ABS), code 1 (ABS_Y), value 7987
Event: time 1492004467.303023, -------------- SYN_REPORT ------------

```

Is there any way to remap it somehow?

---

