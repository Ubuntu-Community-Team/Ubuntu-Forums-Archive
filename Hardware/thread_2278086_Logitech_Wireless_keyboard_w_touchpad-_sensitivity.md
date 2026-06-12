---
title: "Logitech Wireless keyboard w/ touchpad- sensitivity settings?"
date: 2015-05-13
forum: Hardware
---

### Post by emarkay on 2015-05-13
Touchpad is slow - very slow. How to permanently change response and movement time? Settings option show nothing for the touchpad.
Thanks!


```
Device 'Logitech Unifying Device. Wireless PID:4024':
    Device Enabled (143):    1
    Coordinate Transformation Matrix (145):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (267):    0
    Device Accel Constant Deceleration (268):    1.000000
    Device Accel Adaptive Deceleration (269):    1.000000
    Device Accel Velocity Scaling (270):    10.000000
    Device Product ID (259):    1133, 50475
    Device Node (260):    "/dev/input/event4"
    Evdev Axis Inversion (271):    0, 0
    Evdev Axes Swap (273):    0
    Axis Labels (274):    "Rel X" (153), "Rel Y" (154), "Rel Horiz Wheel" (265), "Rel Dial" (293), "Rel Vert Wheel" (266)
    Button Labels (275):    "Button Left" (146), "Button Middle" (147), "Button Right" (148), "Button Wheel Up" (149), "Button Wheel Down" (150), "Button Horiz Wheel Left" (151), "Button Horiz Wheel Right" (152), "Button Side" (263), "Button Extra" (264), "Button Forward" (290), "Button Back" (291), "Button Task" (292), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262)
    Evdev Scrolling Distance (276):    1, 1, 1
    Evdev Middle Button Emulation (277):    0
    Evdev Middle Button Timeout (278):    50
    Evdev Third Button Emulation (279):    0
    Evdev Third Button Emulation Timeout (280):    1000
    Evdev Third Button Emulation Button (281):    3
    Evdev Third Button Emulation Threshold (282):    20
    Evdev Wheel Emulation (283):    0
    Evdev Wheel Emulation Axes (284):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (285):    10
    Evdev Wheel Emulation Timeout (286):    200
    Evdev Wheel Emulation Button (287):    4
    Evdev Drag Lock Buttons (288):    0


```

---

### Post by dino99 on 2015-05-14
its not a joke, but do you "sometime" clean the touchpad ?

---

### Post by efflandt on 2015-05-15
Do Settings > **Mouse & Touchpad** not do anything. A touchpad is basically treated like a mouse, so double-click or speed settings would apply to either.

---

### Post by emarkay on 2015-07-21
There are no settings for a touchpad.

---

### Post by linfidel on 2016-05-02
There are, apparently, no settings for mouse, either, at least not with 14.04 or 16.04 live CD.

---

### Post by him610 on 2016-05-02
> There are no settings for a touchpad.
In Xubuntu 16.04, not sure about other 'buntus

Settings > Mouse and Touchpad  - there on tab, Devices you can ID your device & adjust Acceleration & Sensitivity

---

### Post by linfidel on 2016-05-02
> **him610 said:**
> In Xubuntu 16.04, not sure about other 'buntus

Settings > Mouse and Touchpad  - there on tab, Devices you can ID your device & adjust Acceleration & Sensitivity
What I have learned since is that this setting often is not available, depending on mouse.  I have a Microsoft wireless (USB) mouse, which doesn't have the setting.  

There has been a bug report for a few years now, but evidently, it has been verified but not fixed.  Someone said that some mice don't report themselves in the manner expected, but since the mouse works when plugged in with no problem, I can't see how that is such a big deal.

What I discovered today is that it depends on the mouse.  I plugged in my old Microsoft wired USB mouse, and the setting appeared.  Then, I tried my old Logitech USB wireless mouse transceiver without the mouse connected, and it too had the setting.  So, I leave it plugged in now, hidden away in back of the computer, and I get the settings.

---

