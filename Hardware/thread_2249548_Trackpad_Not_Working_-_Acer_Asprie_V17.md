---
title: "Trackpad Not Working - Acer Asprie V17"
date: 2014-10-23
forum: Hardware
---

### Post by barrycarey on 2014-10-23
Hey all,

I'm having a bit of a strange issue with my new laptop.  It's an Acer Asprie V17 Black Edition.  Today I configured a dualboot with Windows 8.1 and Ubuntu 14.04.  I noticed straight away the trackpad wasn't working during the Ubuntu install so I proceeded with a USB mouse. 

I have gone through pretty much every trackpad related thread I can find but have not found a solution. 

I do have trackpad settings under the settings menu but not input from it is recognised. 

xinput output

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627;                                             id=13    [slave  pointer  (2)]
&#9116;   &#8627; Logitech G9x Laser Mouse                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; Logitech G9x Laser Mouse                    id=12    [slave  pointer  (2)]

```

I believe device ID 13 is the trackpad. 

xinput --watch-props 13 Output

```
Device Enabled (135):    1
    Coordinate Transformation Matrix (137):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (263):    1
    Device Accel Constant Deceleration (264):    2.500000
    Device Accel Adaptive Deceleration (265):    1.000000
    Device Accel Velocity Scaling (266):    12.500000
    Synaptics Edges (287):    49, 1187, 48, 850
    Synaptics Finger (288):    25, 30, 0
    Synaptics Tap Time (289):    180
    Synaptics Tap Move (290):    67
    Synaptics Tap Durations (291):    180, 180, 100
    Synaptics ClickPad (292):    0
    Synaptics Middle Button Timeout (293):    75
    Synaptics Two-Finger Pressure (294):    282
    Synaptics Two-Finger Width (295):    7
    Synaptics Scrolling Distance (296):    30, 30
    Synaptics Edge Scrolling (297):    0, 0, 0
    Synaptics Two-Finger Scrolling (298):    1, 1
    Synaptics Move Speed (299):    1.000000, 1.750000, 0.130976, 0.000000
    Synaptics Off (300):    0
    Synaptics Locked Drags (301):    0
    Synaptics Locked Drags Timeout (302):    5000
    Synaptics Tap Action (303):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (304):    1, 3, 0
    Synaptics Circular Scrolling (305):    0
    Synaptics Circular Scrolling Distance (306):    0.100000
    Synaptics Circular Scrolling Trigger (307):    0
    Synaptics Circular Pad (308):    0
    Synaptics Palm Detection (309):    0
    Synaptics Palm Dimensions (310):    10, 200
    Synaptics Coasting Speed (311):    20.000000, 50.000000
    Synaptics Pressure Motion (312):    30, 160
    Synaptics Pressure Motion Factor (313):    1.000000, 1.000000
    Synaptics Resolution Detect (314):    1
    Synaptics Grab Event Device (315):    1
    Synaptics Gestures (316):    1
    Synaptics Capabilities (317):    1, 0, 0, 1, 1, 0, 0
    Synaptics Pad Resolution (318):    12, 12
    Synaptics Area (319):    0, 0, 0, 0
    Synaptics Noise Cancellation (320):    7, 7
    Device Product ID (252):    1739, 10608
    Device Node (253):    "/dev/input/event14"
```



Does anyone have any suggestions as to why this would be happening?  I'm happy to provide any additonal details if required. 

Thank you

---

