---
title: "Logitech G500s not working properly (10th button not responding)"
date: 2016-08-30
forum: Hardware
---

### Post by alexdd21 on 2016-08-30
Hi guys,

I'm trying to understand and fix the following issue: the 10th button of my logitech g500s is not working, xev nor xinput -test 11 show anything for the 10th button.:(

$ xinput -list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; EST Gaming keyboard                         id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech G500s Laser Gaming Mouse           id=11    [slave  pointer  (2)]
&#9116;   &#8627; Logitech G500s Laser Gaming Mouse           id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; EST Gaming keyboard                         id=8    [slave  keyboard (3)]
    &#8627; EST Gaming keyboard                         id=10    [slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                          id=13    [slave  keyboard (3)]



$ xinput list-props #11
Device 'Logitech G500s Laser Gaming Mouse':
    Device Enabled (143):    1
    Coordinate Transformation Matrix (145):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (270):    0
    Device Accel Constant Deceleration (271):    1.000000
    Device Accel Adaptive Deceleration (272):    1.000000
    Device Accel Velocity Scaling (273):    10.000000
    Device Product ID (264):    1133, 49742
    Device Node (265):    "/dev/input/event2"
    Evdev Axis Inversion (274):    0, 0
    Evdev Axes Swap (276):    0
    Axis Labels (277):    "Rel X" (153), "Rel Y" (154), "Rel Horiz Wheel" (269), "Rel Vert Wheel" (297)
    Button Labels (278):    "Button Left" (146), "Button Middle" (147), "Button Right" (148), "Button Wheel Up" (149), "Button Wheel Down" (150), "Button Horiz Wheel Left" (151), "Button Horiz Wheel Right" (152), "Button Side" (292), "Button Extra" (293), "Button Forward" (294), "Button Back" (295), "Button Task" (296), "Button Unknown" (267), "Button Unknown" (267), "Button Unknown" (267), "Button Unknown" (267), "Button Unknown" (267), "Button Unknown" (267), "Button Unknown" (267), "Button Unknown" (267), "Button Unknown" (267), "Button Unknown" (267), "Button Unknown" (267), "Button Unknown" (267)
    Evdev Scrolling Distance (279):    1, 1, 1
    Evdev Middle Button Emulation (280):    0
    Evdev Middle Button Timeout (281):    50
    Evdev Third Button Emulation (282):    0
    Evdev Third Button Emulation Timeout (283):    1000
    Evdev Third Button Emulation Button (284):    3
    Evdev Third Button Emulation Threshold (285):    20
    Evdev Wheel Emulation (286):    0
    Evdev Wheel Emulation Axes (287):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (288):    10
    Evdev Wheel Emulation Timeout (289):    200
    Evdev Wheel Emulation Button (290):    4
    Evdev Drag Lock Buttons (291):    0

$ xinput list-props 12
Device 'Logitech G500s Laser Gaming Mouse':
    Device Enabled (143):    1
    Coordinate Transformation Matrix (145):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (270):    0
    Device Accel Constant Deceleration (271):    1.000000
    Device Accel Adaptive Deceleration (272):    1.000000
    Device Accel Velocity Scaling (273):    10.000000
    Device Product ID (264):    1133, 49742
    Device Node (265):    "/dev/input/event3"
    Evdev Axis Inversion (274):    0, 0
    Evdev Axes Swap (276):    0
    Axis Labels (277):    "Rel X" (153), "Rel Y" (154), "Rel Horiz Wheel" (269)
    Button Labels (278):    "Button 0" (268), "Button Unknown" (267), "Button Unknown" (267), "Button Wheel Up" (149), "Button Wheel Down" (150), "Button Horiz Wheel Left" (151), "Button Horiz Wheel Right" (152)
    Evdev Scrolling Distance (279):    1, 1, 1
    Evdev Middle Button Emulation (280):    0
    Evdev Middle Button Timeout (281):    50
    Evdev Third Button Emulation (282):    0
    Evdev Third Button Emulation Timeout (283):    1000
    Evdev Third Button Emulation Button (284):    3
    Evdev Third Button Emulation Threshold (285):    20
    Evdev Wheel Emulation (286):    0
    Evdev Wheel Emulation Axes (287):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (288):    10
    Evdev Wheel Emulation Timeout (289):    200
    Evdev Wheel Emulation Button (290):    4
    Evdev Drag Lock Buttons (291):    0

---

