---
title: "Middle Mouse Button not working"
date: 2016-11-16
forum: Hardware
---

### Post by madtom1999 on 2016-11-16
I've got a Logitech RX 250 optical mouse and cant get the middle mouse/scroll wheel click working
**xinput --list**
gives:------------------------------

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Chicony USB 2.0 Camera                      id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

-------------------------------------

and **$ xinput --list-props 'Logitech USB-PS/2 Optical Mouse'**
gives:

--------------------------------------

Device 'Logitech USB-PS/2 Optical Mouse':
    Device Enabled (137):    1
    Coordinate Transformation Matrix (139):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (268):    0
    Device Accel Constant Deceleration (269):    1.000000
    Device Accel Adaptive Deceleration (270):    1.000000
    Device Accel Velocity Scaling (271):    10.000000
    Device Product ID (257):    1133, 49232
    Device Node (258):    "/dev/input/event7"
    Evdev Axis Inversion (272):    0, 0
    Evdev Axes Swap (274):    0
    Axis Labels (275):    "Rel X" (147), "Rel Y" (148), "Rel Horiz Wheel" (266), "Rel Vert Wheel" (267)
    Button Labels (276):    "Button Left" (140), "Button Middle" (141), "Button Right" (142), "Button Wheel Up" (143), "Button Wheel Down" (144), "Button Horiz Wheel Left" (145), "Button Horiz Wheel Right" (146), "Button Side" (261), "Button Extra" (262), "Button Forward" (263), "Button Back" (264), "Button Task" (265), "Button Unknown" (260), "Button Unknown" (260), "Button Unknown" (260), "Button Unknown" (260)
    Evdev Scrolling Distance (277):    1, 1, 1
    Evdev Middle Button Emulation (278):    0
    Evdev Middle Button Timeout (279):    50
    Evdev Third Button Emulation (280):    0
    Evdev Third Button Emulation Timeout (281):    1000
    Evdev Third Button Emulation Button (282):    3
    Evdev Third Button Emulation Threshold (283):    20
    Evdev Wheel Emulation (284):    0
    Evdev Wheel Emulation Axes (285):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (286):    10
    Evdev Wheel Emulation Timeout (287):    200
    Evdev Wheel Emulation Button (288):    4
    Evdev Drag Lock Buttons (289):    0

------------------------------------------------------- 
**xev -event mouse| grep Button --before-context=1 --after-context=2**

and I get all the buttons (including rocking the scroll wheel left and right) but not the 'Button Middle' 
I have no .Xmodmap file so where is the Button Middle gone?

---

### Post by madtom1999 on 2016-11-18
Seems this is down to a bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1581088](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1581088)
Hope this gets fixed soon - otherwise there will be a lot of Steam users annoyed with Ubuntu!

---

