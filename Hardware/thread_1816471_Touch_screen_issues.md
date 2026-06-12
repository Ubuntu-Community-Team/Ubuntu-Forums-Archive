---
title: "Touch screen issues"
date: 2011-08-02
forum: Hardware
---

### Post by kpike on 2011-08-02
Hello,

I am new to Ubuntu and this forum. I installed Ubuntu 11.04 on my Fujitsu T731. I am having issues with my touch screen. It is capable of finger and pen input. The pen input works just fine but my finger input is not functioning properly. My finger location is recognized properly but when I release my finger from the screen the cursor instantly moves to the top left corner of the screen resulting in highlighting text and attempts to move windows. I would like to fix this.

xinput list:
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Pen                                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; ISD-V4 Finger                               id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                             id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=9    [slave  keyboard (3)]
    &#8627; Power Button                                id=10    [slave  keyboard (3)]
    &#8627; CNF8248                                     id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

xinput list-props "ISD-V4 Finger"
Device 'ISD-V4 Finger':
    Device Enabled (127):    1
    Coordinate Transformation Matrix (129):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (244):    0
    Device Accel Constant Deceleration (245):    1.000000
    Device Accel Adaptive Deceleration (246):    1.000000
    Device Accel Velocity Scaling (247):    10.000000
    Evdev Axis Inversion (435):    0, 0
    Evdev Axis Calibration (436):    <no items>
    Evdev Axes Swap (437):    0
    Axis Labels (438):    "Abs X" (431), "Abs Y" (432), "Abs Pressure" (433), "Abs Misc" (434)
    Button Labels (439):    "Button Unknown" (430), "Button Unknown" (430), "Button Unknown" (430), "Button Wheel Up" (133), "Button Wheel Down" (134)
    Evdev Middle Button Emulation (440):    0
    Evdev Middle Button Timeout (441):    50
    Evdev Wheel Emulation (442):    0
    Evdev Wheel Emulation Axes (443):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (444):    10
    Evdev Wheel Emulation Timeout (445):    200
    Evdev Wheel Emulation Button (446):    4
    Evdev Drag Lock Buttons (447):    0

---

### Post by kpike on 2011-08-03
The issue was solved by updating the wacom driver (xf86-input-wacom 0.11.1) and adding "ISD-V4" under Match Products in the 50.wacom.conf file. I found the solution reading this thread:

[http://ubuntuforums.org/showthread.php?t=1785015](http://ubuntuforums.org/showthread.php?t=1785015)

---

### Post by Favux on 2011-08-03
Hi kpike,

Welcome to Ubuntu forums!

Nice job.  I gather the Wacom line in the *lsusb* output shows the digitizer is the E6?  So now there are two tablet PCs with the E6, the Lenovo X200t and the Fujitsu T731.

---

