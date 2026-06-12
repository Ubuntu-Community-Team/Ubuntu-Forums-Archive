---
title: "How to disable simultaneous left and right on mouse?"
date: 2017-02-14
forum: Hardware
---

### Post by mika2salo on 2017-02-14
I'm playing insurgency on my linux and I have shooting linked to left mouse button and aiming to right.
When I press left to start to shoot and shortly after right, it registers it as one mouse click and stops shooting.

I'm not sure what action left and right simultanous click is emulating but is there any way to turn it off?

My mouse is Razer Deathadder and **xinput** gives info

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer DeathAdder Chroma               id=9    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer DeathAdder Chroma               id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Razer Razer DeathAdder Chroma               id=10    [slave  keyboard (3)]
    &#8627; CM Storm Quickfire TKL 6keys                id=11    [slave  keyboard (3)]
    &#8627; CM Storm Quickfire TKL 6keys                id=12    [slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                          id=13    [slave  keyboard (3)]

**xinput list-props 9**


Device 'Razer Razer DeathAdder Chroma':
    Device Enabled (151):    1
    Coordinate Transformation Matrix (153):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (275):    0
    Device Accel Constant Deceleration (276):    1.000000
    Device Accel Adaptive Deceleration (277):    1.000000
    Device Accel Velocity Scaling (278):    10.000000
    Device Product ID (269):    5426, 67
    Device Node (270):    "/dev/input/event4"
    Evdev Axis Inversion (279):    0, 0
    Evdev Axes Swap (281):    0
    Axis Labels (282):    "Rel X" (161), "Rel Y" (162), "Rel Horiz Wheel" (274)
    Button Labels (283):    "Button 0" (273), "Button Unknown" (272), "Button Unknown" (272), "Button Wheel Up" (157), "Button Wheel Down" (158), "Button Horiz Wheel Left" (159), "Button Horiz Wheel Right" (160)
    Evdev Scrolling Distance (284):    1, 1, 1
    Evdev Middle Button Emulation (285):    1
    Evdev Middle Button Timeout (286):    50
    Evdev Third Button Emulation (287):    0
    Evdev Third Button Emulation Timeout (288):    1000
    Evdev Third Button Emulation Button (289):    3
    Evdev Third Button Emulation Threshold (290):    20
    Evdev Wheel Emulation (291):    0
    Evdev Wheel Emulation Axes (292):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (293):    10
    Evdev Wheel Emulation Timeout (294):    200
    Evdev Wheel Emulation Button (295):    4
    Evdev Drag Lock Buttons (296):    0

**xinput list-props 14**

Device 'Razer Razer DeathAdder Chroma':
    Device Enabled (151):    1
    Coordinate Transformation Matrix (153):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (275):    0
    Device Accel Constant Deceleration (276):    1.000000
    Device Accel Adaptive Deceleration (277):    1.000000
    Device Accel Velocity Scaling (278):    10.000000
    Device Product ID (269):    5426, 67
    Device Node (270):    "/dev/input/event3"
    Evdev Axis Inversion (279):    0, 0
    Evdev Axes Swap (281):    0
    Axis Labels (282):    "Rel X" (161), "Rel Y" (162), "Rel Vert Wheel" (369)
    Button Labels (283):    "Button Left" (154), "Button Middle" (155), "Button Right" (156), "Button Wheel Up" (157), "Button Wheel Down" (158), "Button Horiz Wheel Left" (159), "Button Horiz Wheel Right" (160), "Button Side" (367), "Button Extra" (368), "Button Unknown" (272), "Button Unknown" (272), "Button Unknown" (272), "Button Unknown" (272)
    Evdev Scrolling Distance (284):    1, 1, 1
    Evdev Middle Button Emulation (285):    1
    Evdev Middle Button Timeout (286):    50
    Evdev Third Button Emulation (287):    0
    Evdev Third Button Emulation Timeout (288):    1000
    Evdev Third Button Emulation Button (289):    3
    Evdev Third Button Emulation Threshold (290):    20
    Evdev Wheel Emulation (291):    0
    Evdev Wheel Emulation Axes (292):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (293):    10
    Evdev Wheel Emulation Timeout (294):    200
    Evdev Wheel Emulation Button (295):    4
    Evdev Drag Lock Buttons (296):    0

I have tested :
**xinput set-button-map**

on both id:s and it i can disable all buttons from mouse but not the simultanous clicking action, so i think its not related to button mappings

---

