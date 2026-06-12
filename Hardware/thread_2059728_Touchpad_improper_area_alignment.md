---
title: "Touchpad improper area alignment"
date: 2012-09-18
forum: Hardware
---

### Post by Frozen Forest on 2012-09-18
EDIT:
Found the problem, was related to the kernel 3.2.0-30, found a few bug reports also
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1046504](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1046504)
[https://patchwork.kernel.org/patch/1283051/](https://patchwork.kernel.org/patch/1283051/)

I recently reinstalled ubuntu 12.04 on my computer, with this installation did a new error/bug occur. The touchpad do work but not the full area, the scroll that should be located at the right edge of it, is instead located 1cm into the touchpad.

I made a very simple picture of the problem, the arrow indicates where the scroll is at the moment. Would it be possible to fix this problem, reconfigure the area or something?

```

$ xinput --list --long
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
    Reporting 7 classes:
        Class originated from: 13. Type: XIButtonClass
        Buttons supported: 12
        Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" "Button Side" "Button Extra" "Button Forward" "Button Back" "Button Task"
        Button state:
        Class originated from: 13. Type: XIValuatorClass
        Detail for Valuator 0:
          Label: Rel X
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 13. Type: XIValuatorClass
        Detail for Valuator 1:
          Label: Rel Y
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 13. Type: XIValuatorClass
        Detail for Valuator 2:
          Label: Rel Horiz Wheel
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 13. Type: XIValuatorClass
        Detail for Valuator 3:
          Label: Rel Vert Wheel
          Range: -1.000000 - -1.000000
          Resolution: 1 units/m
          Mode: relative
        Class originated from: 13. Type: XIScrollClass
        Scroll info for Valuator 2
          type: 2 (horizontal)
          increment: 1.000000
          flags: 0x0
        Class originated from: 13. Type: XIScrollClass
        Scroll info for Valuator 3
          type: 1 (vertical)
          increment: -1.000000
          flags: 0x2 ( preferred )

&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
    Reporting 3 classes:
        Class originated from: 4. Type: XIButtonClass
        Buttons supported: 10
        Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" None None None
        Button state:
        Class originated from: 4. Type: XIValuatorClass
        Detail for Valuator 0:
          Label: Rel X
          Range: -1.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 4. Type: XIValuatorClass
        Detail for Valuator 1:
          Label: Rel Y
          Range: -1.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative

&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
    Reporting 7 classes:
        Class originated from: 12. Type: XIButtonClass
        Buttons supported: 12
        Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" None None None None None
        Button state:
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 0:
          Label: Rel X
          Range: 1472.000000 - 5472.000000
          Resolution: 81000 units/m
          Mode: relative
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 1:
          Label: Rel Y
          Range: 1408.000000 - 4448.000000
          Resolution: 95000 units/m
          Mode: relative
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 2:
          Label: Rel Horiz Scroll
          Range: 0.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 12. Type: XIValuatorClass
        Detail for Valuator 3:
          Label: Rel Vert Scroll
          Range: 0.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 12. Type: XIScrollClass
        Scroll info for Valuator 2
          type: 2 (horizontal)
          increment: 100.000000
          flags: 0x0
        Class originated from: 12. Type: XIScrollClass
        Scroll info for Valuator 3
          type: 1 (vertical)
          increment: 100.000000
          flags: 0x0

``````
$ xinput --list-props 12
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (130):    1
    Coordinate Transformation Matrix (132):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (254):    1
    Device Accel Constant Deceleration (255):    2.500000
    Device Accel Adaptive Deceleration (256):    1.000000
    Device Accel Velocity Scaling (257):    12.500000
    Synaptics Edges (258):    1752, 5192, 1620, 4236
    Synaptics Finger (259):    25, 30, 256
    Synaptics Tap Time (260):    180
    Synaptics Tap Move (261):    221
    Synaptics Tap Durations (262):    180, 180, 100
    Synaptics ClickPad (263):    0
    Synaptics Tap FastTap (264):    0
    Synaptics Middle Button Timeout (265):    75
    Synaptics Two-Finger Pressure (266):    282
    Synaptics Two-Finger Width (267):    7
    Synaptics Scrolling Distance (268):    100, 100
    Synaptics Edge Scrolling (269):    1, 0, 0
    Synaptics Two-Finger Scrolling (270):    0, 0
    Synaptics Move Speed (271):    1.000000, 1.750000, 0.039809, 40.000000
    Synaptics Edge Motion Pressure (272):    30, 160
    Synaptics Edge Motion Speed (273):    1, 401
    Synaptics Edge Motion Always (274):    0
    Synaptics Off (275):    2
    Synaptics Locked Drags (276):    0
    Synaptics Locked Drags Timeout (277):    5000
    Synaptics Tap Action (278):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (279):    1, 1, 0
    Synaptics Circular Scrolling (280):    0
    Synaptics Circular Scrolling Distance (281):    0.100000
    Synaptics Circular Scrolling Trigger (282):    0
    Synaptics Circular Pad (283):    0
    Synaptics Palm Detection (284):    0
    Synaptics Palm Dimensions (285):    10, 200
    Synaptics Coasting Speed (286):    20.000000, 50.000000
    Synaptics Pressure Motion (287):        ... of unknown type CARDINAL

    Synaptics Pressure Motion Factor (288):    1.000000, 1.000000
    Synaptics Resolution Detect (289):    1
    Synaptics Grab Event Device (290):    1
    Synaptics Gestures (291):    1
    Synaptics Capabilities (292):    1, 0, 1, 1, 1, 1, 1
    Synaptics Pad Resolution (293):    95, 81
    Synaptics Area (294):    0, 0, 0, 0
    Synaptics Noise Cancellation (295):    25, 25
    Device Product ID (249):    2, 7
    Device Node (250):    "/dev/input/event7"


```

---

