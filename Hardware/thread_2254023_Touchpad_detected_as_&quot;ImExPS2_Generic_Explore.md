---
title: "Touchpad detected as &quot;ImExPS/2 Generic Explorer Mouse&quot;"
date: 2014-11-24
forum: Hardware
---

### Post by Johan_Frisk on 2014-11-24
Hello! I was hoping i could get some assistance in solving an issue wih my laptop, everything works great except using edge-scrolling upwards using the touchpad.

Scrolling down works as expected but whenever i try to scroll up it just scrolls down really quickly instead. Tap to cick is also working and the touchpad is not multitouch. Im having this issue with every version of Linux I've tried so far, Kernel versions 3.13, 3.16 and 3.18RC5. The module used is psmouse, unloading it prevents the touchpad from working and loading it again makes the touchpad work. Unfortunaly I'm unsure of the make and brand of the touchpad but I'm pretty sure it's not elantech or synaptic. I would have thought this touchpad couldn't be used with Linux if it wasn't for scrolling downward and taptoclick working, as scrolling up and down works as expected in Windows 8 I'm hopeful I can somehow get it working.

Using xev to look at which events are created when i scroll up and down using the trackpad it seems like the same event is produced when i scroll up as down (button 5 pressed and released):
```
ButtonPress event, serial 37, synthetic NO, window 0x2e00001,
    root 0x9d, subw 0x0, time 729771, (58,101), root:(59,913),
    state 0x0, button 5, same_screen YES

ButtonRelease event, serial 37, synthetic NO, window 0x2e00001,
    root 0x9d, subw 0x0, time 729771, (58,101), root:(59,913),
    state 0x1000, button 5, same_screen YES

ButtonPress event, serial 37, synthetic NO, window 0x2e00001,
    root 0x9d, subw 0x0, time 729771, (58,101), root:(59,913),
    state 0x0, button 5, same_screen YES

ButtonRelease event, serial 37, synthetic NO, window 0x2e00001,
    root 0x9d, subw 0x0, time 729771, (58,101), root:(59,913),
    state 0x1000, button 5, same_screen YES


```


xinput output:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]When 
&#9116;   &#8627; ImExPS/2 Generic Explorer Mouse             id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB_2.0_Webcam                              id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]


```

Ive tried messing around with these settings some but it didn't help really. These are the default settings:
```
xinput watch-props 12
Device 'ImExPS/2 Generic Explorer Mouse':
    Device Enabled (134):    1
    Coordinate Transformation Matrix (136):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (261):    0
    Device Accel Constant Deceleration (262):    1.000000
    Device Accel Adaptive Deceleration (263):    1.000000
    Device Accel Velocity Scaling (264):    10.000000
    Device Product ID (253):    2, 6
    Device Node (254):    "/dev/input/event9"
    Evdev Axis Inversion (265):    0, 0
    Evdev Axes Swap (267):    0
    Axis Labels (268):    "Rel X" (144), "Rel Y" (145), "Rel Horiz Wheel" (259), "Rel Vert Wheel" (260)
    Button Labels (269):    "Button Left" (137), "Button Middle" (138), "Button Right" (139), "Button Wheel Up" (140), "Button Wheel Down" (141), "Button Horiz Wheel Left" (142), "Button Horiz Wheel Right" (143), "Button Side" (257), "Button Extra" (258), "Button Unknown" (256), "Button Unknown" (256), "Button Unknown" (256), "Button Unknown" (256)
    Evdev Middle Button Emulation (270):    0
    Evdev Middle Button Timeout (271):    50
    Evdev Third Button Emulation (272):    0
    Evdev Third Button Emulation Timeout (273):    1000
    Evdev Third Button Emulation Button (274):    3
    Evdev Third Button Emulation Threshold (275):    20
    Evdev Wheel Emulation (276):    0
    Evdev Wheel Emulation Axes (277):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (278):    10
    Evdev Wheel Emulation Timeout (279):    200
    Evdev Wheel Emulation Button (280):    4
    Evdev Drag Lock Buttons (281):    0


```

the device looks like this when i cat /proc/bus/inputs
```
I: Bus=0011 Vendor=0002 Product=0006 Version=0000
N: Name="ImExPS/2 Generic Explorer Mouse"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input11
U: Uniq=
H: Handlers=mouse0 event9 
B: PROP=0
B: EV=7
B: KEY=1f0000 0 0 0 0
B: REL=143


```

I would be really thankful if someone would help me out to get this working properly. Please let me know if you have any suggestions that might be able to get downward scrlling working correctly. I'd be more than willing to provide more information about my system or output from any commands I haven't included in this post. Thanks

---

