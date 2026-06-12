---
title: "Drawing tablet pen hover stops after writing with certain pressure"
date: 2018-01-14
forum: Hardware
---

### Post by arsen.za on 2018-01-14
I have xp-pen star 06 graphics tablet, I am trying to configure the tablet and I am making a slow progress, Now I have faced the following problem.


When I hover the pen over the tablet the mouse moves normally but when I start writing on the tablet with certain pressure the hover effect stops and then the tablet cursor acts like mouse down, when you write on the tablet the cursor jumps to then pen position.
**I am using evdev driver**
Any help to fix this issue will be appreciated
```

Device 'XP-PEN STAR 06':
    Device Enabled (141):   1
    Coordinate Transformation Matrix (143): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (277): 0
    Device Accel Constant Deceleration (278):   1.000000
    Device Accel Adaptive Deceleration (279):   1.000000
    Device Accel Velocity Scaling (280):    10.000000
    Device Product ID (268):    10429, 120
    Device Node (267):  "/dev/input/event1"
    Evdev Axis Inversion (281): 0, 0
    Evdev Axis Calibration (282):   <no items>
    Evdev Axes Swap (283):  0
    Axis Labels (284):  "Abs X" (274), "Abs Y" (275), "Abs Pressure" (276), "Rel Vert Wheel" (273)
    Button Labels (285):    "Button Left" (144), "Button Middle" (145), "Button Right" (146), "Button Wheel Up" (147), "Button Wheel Down" (148), "Button Horiz Wheel Left" (149), "Button Horiz Wheel Right" (150), "Button Side" (270), "Button Extra" (271), "Button Forward" (272), "Button Unknown" (269), "Button Unknown" (269), "Button Unknown" (269), "Button Unknown" (269)
    Evdev Scrolling Distance (286): 1, 1, 1
    Evdev Middle Button Emulation (287):    0
    Evdev Middle Button Timeout (288):  50
    Evdev Middle Button Button (289):   2
    Evdev Third Button Emulation (290): 0
    Evdev Third Button Emulation Timeout (291): 1000
    Evdev Third Button Emulation Button (292):  3
    Evdev Third Button Emulation Threshold (293):   20
    Evdev Wheel Emulation (294):    0
    Evdev Wheel Emulation Axes (295):   0, 0, 4, 5
    Evdev Wheel Emulation Inertia (296):    10
    Evdev Wheel Emulation Timeout (297):    200
    Evdev Wheel Emulation Button (298): 4
    Evdev Drag Lock Buttons (299):  0

```
**evtest**
```

Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x28bd product 0x78 version 0x100
Input device name: "XP-PEN STAR 06"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 272 (BTN_LEFT)
    Event code 273 (BTN_RIGHT)
    Event code 274 (BTN_MIDDLE)
    Event code 275 (BTN_SIDE)
    Event code 276 (BTN_EXTRA)
    Event code 277 (BTN_FORWARD)
    Event code 330 (BTN_TOUCH)
  Event type 2 (EV_REL)
    Event code 0 (REL_X)
    Event code 1 (REL_Y)
    Event code 8 (REL_WHEEL)
    Event code 9 (REL_MISC)
  Event type 3 (EV_ABS)
    Event code 0 (ABS_X)
      Value  11118
      Min        0
      Max    32767
    Event code 1 (ABS_Y)
      Value  20792
      Min        0
      Max    32767
    Event code 24 (ABS_PRESSURE)
      Value      0
      Min        0
      Max     8191
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
Properties:
Testing ... (interrupt to exit)

```
In evtest I can see events while the pen is hover over the tablet but the mouse is not moving.


here xinput test output while the problem acquired, the motion stops.
**xinput test**
```

motion a[0]=13106 a[1]=23209 
motion a[0]=13081 a[1]=23244 
motion a[0]=13051 
motion a[0]=13014 a[1]=23281 
motion a[0]=12995 
motion a[0]=12979 
motion a[0]=12966 
motion a[0]=12951 a[1]=23247 
motion a[0]=12941 a[1]=23215 
motion a[0]=12928 
motion a[0]=12917 
motion a[0]=12913 a[1]=23215 a[2]=3167 
button press   1 
motion a[0]=12910 a[1]=23215 a[2]=3218 
motion a[0]=12908 a[1]=23215 a[2]=3725 
motion a[0]=12906 a[1]=23215 a[2]=4183 
motion a[2]=4679 
motion a[0]=12904 a[1]=23215 a[2]=5131 
motion a[2]=5553 
motion a[1]=23183 a[2]=5904 
motion a[2]=6516 
motion a[2]=6737 
motion a[2]=6950 
motion a[2]=7152 
motion a[2]=7379 
motion a[0]=12920 a[1]=23183 a[2]=7829 
motion a[2]=8001 
motion a[2]=8114 
motion a[2]=8176 
motion a[2]=8191 
motion a[0]=12908 
motion a[1]=23154 
motion a[0]=12901 
motion a[2]=7784 
motion a[0]=12895 a[1]=23119 a[2]=7234 
motion a[0]=12888 a[1]=23094 a[2]=6407 
motion a[0]=12880 a[1]=23063 a[2]=5254 
motion a[0]=12870 a[1]=23031 a[2]=3814 
motion a[0]=12849 a[1]=22950 a[2]=1095 
button release 1

```

---

### Post by tianzhun on 2018-10-31
you may can ask their Technical Support for help , xp-pen star 06 offical site: [https://www.xp-pen.com/goods/show/id/194.html](https://www.xp-pen.com/goods/show/id/194.html)

---

