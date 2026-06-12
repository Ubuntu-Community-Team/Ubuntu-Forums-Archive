---
title: "Logitech G500 Mouse Issue in Xinput"
date: 2012-12-20
forum: Hardware
---

### Post by Jtricx on 2012-12-20
So I decided to use my logitech mouse on Ubuntu now that I got the steam beta.  However, when using the mouse i noticed the acceleration is never completely removed by ubuntu's mouse setting program.  

So I then decided to just modify it in xinput. However when listing devices i got these results: 

```
:~$ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech G500                             id=8    [slave  pointer  (2)]
&#9116;   &#8627; Logitech G500                             id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Logitech Illuminated Keyboard    id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Logitech Logitech Illuminated Keyboard    id=10   [slave  keyboard (3)]
    &#8627; Monitor Webcam                            id=12   [slave  keyboard (3)]

```


My goal was to write a script to modify it at start up, but I can't use the "name" because two of the same device are listed and if i use the "id" for either it works.
```
:~$ xinput set-prop 'Logitech G500' 'Device Accel Profile' -1
Warning: There are multiple devices matching 'Logitech G500'.
To ensure the correct one is selected, please use the device ID, or prefix the
device name with 'pointer:' or 'keyboard:' as appropriate.

unable to find device Logitech G500

```

And with a start up script the id's aren't working. 

Thanks everyone!

---

### Post by Ishayu on 2013-02-09
This needs a bump. I have the same problem.

---

### Post by JoZ3 on 2013-10-14
anny??

---

### Post by LaCrem on 2014-01-15
Just type

xinput list-props #device-id

In your case #device-id should be 9

You should get something like this:

```
Device 'Logitech G500':
    Device Enabled (134):    1
    Coordinate Transformation Matrix (136):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
**    Device Accel Profile (264):    0**
    Device Accel Constant Deceleration (265):    1.000000
    Device Accel Adaptive Deceleration (266):    1.000000
    Device Accel Velocity Scaling (267):    10.000000
    Device Product ID (253):    1133, 49256
    Device Node (254):    "/dev/input/event5"
    Evdev Axis Inversion (268):    0, 0
    Evdev Axes Swap (270):    0
    Axis Labels (271):    "Rel X" (144), "Rel Y" (145), "Rel Horiz Wheel" (262)
    Button Labels (272):    "Button 0" (285), "Button Unknown" (256), "Button Unknown" (256), "Button Wheel Up" (140), "Button Wheel Down" (141), "Button Horiz Wheel Left" (142), "Button Horiz Wheel Right" (143)
    Evdev Middle Button Emulation (273):    0
    Evdev Middle Button Timeout (274):    50
    Evdev Third Button Emulation (275):    0
    Evdev Third Button Emulation Timeout (276):    1000
    Evdev Third Button Emulation Button (277):    3
    Evdev Third Button Emulation Threshold (278):    20
    Evdev Wheel Emulation (279):    0
    Evdev Wheel Emulation Axes (280):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (281):    10
    Evdev Wheel Emulation Timeout (282):    200
    Evdev Wheel Emulation Button (283):    4
    Evdev Drag Lock Buttons (284):    0
```

You should use

xinput set-prop #device-id #property-id #value

Where:
#device-id in your case should be 9
#property-id in the output sample is 264, in your case could be different
#value could be:
[QUOTE=superuser.com]-1: none no velocity-dependent pointer acceleration or deceleration. If constant deceleration is also unused, motion processing is suppressed, saving some cycles.
0: classic (the default) similar to old behaviour, but more predictable. Selects between 'polynomial' and 'simple' based on threshold =/!= 0.
1: device-dependent available if the hardware driver installs it. May be coming for synaptics.
2: polynomial Scales polynomial: velocity serves as the coefficient, acceleration being the exponent. Very useable, the recommended profile.
3: smooth linear scales mostly linear, but with a smooth (non-linear) start.
4: simple Transitions between accelerated/unaccelerated, but with a smooth transition range. This has the fundamental problem of accelerating on two niveaus, on which acceleration stays independent of velocity. Traditionally the default however.
5: power accelerates by a power function. velocity is the exponent here. Adheres to threshold. Will easily get hard to control, so it is important you have properly tuned your velocity estimation.
6: linear just linear to velocity and acceleration. Simple and clean.
7: limited smoothly ascends to acceleration, maxing out at threshold, where it becomes flat (is limited).[/QUOTE]

---

