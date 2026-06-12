---
title: "Extra mouse button problem"
date: 2017-05-18
forum: Hardware
---

### Post by eev2 on 2017-05-18
I have a mouse with an extra button which causes me problems.
The mouse is seen here
[https://www.amazon.co.uk/Perixx-PERIMICE-515-Wired-Ergonomic-Vertical/dp/B00OTU6VD2](https://www.amazon.co.uk/Perixx-PERIMICE-515-Wired-Ergonomic-Vertical/dp/B00OTU6VD2)
You will notice a button next to the mouse wheel which corresponds to the event XF86HomePage. I don't really need that button but occasionally I will press it by accident and then all hell breaks loose: the event XF86HomePage is called repeatedly, like 100 times, and my computer freezes because it tries to launch 100 firefoxes. I remapped the event to bash -c ":" but I still get a temporary freeze of a couple of minutes. 

I tried to disable the buttons in my .Xmodmap by
pointer = 1 2 3 0 0 0 0 0 0 0 0 0 0
but it didn't work.

I also tried
remove Lock = XF86HomePage
keycode 180 = NoSymbol

Ideally, I would have liked to have that button function, but if not are there any suggestions for disabling that button completely?

Some extra info
```
~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ATWF@83-W001 HID-compliant Mouse            id=11    [slave  pointer  (2)]
&#9116;   &#8627; GASIA USB KB V11                            id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; GASIA USB KB V11                            id=8    [slave  keyboard (3)]
    &#8627; ATWF@83-W001 HID-compliant Mouse            id=10    [slave  keyboard (3)]
~$ xinput list-props 10
Device 'ATWF@83-W001 HID-compliant Mouse':
    Device Enabled (136):    0
    Coordinate Transformation Matrix (138):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Product ID (256):    7511, 7
    Device Node (257):    "/dev/input/event2"
~$ xinput list-props 11
Device 'ATWF@83-W001 HID-compliant Mouse':
    Device Enabled (136):    1
    Coordinate Transformation Matrix (138):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (262):    -1
    Device Accel Constant Deceleration (263):    3.000000
    Device Accel Adaptive Deceleration (264):    1.000000
    Device Accel Velocity Scaling (265):    1.000000
    Device Product ID (256):    7511, 7
    Device Node (257):    "/dev/input/event4"
    Evdev Axis Inversion (266):    0, 0
    Evdev Axes Swap (268):    0
    Axis Labels (269):    "Rel X" (146), "Rel Y" (147), "Rel Horiz Wheel" (261), "Rel Dial" (286), "Rel Vert Wheel" (287)
    Button Labels (270):    "Button Left" (139), "Button Middle" (140), "Button Right" (141), "Button Wheel Up" (142), "Button Wheel Down" (143), "Button Horiz Wheel Left" (144), "Button Horiz Wheel Right" (145), "Button Side" (284), "Button Extra" (285), "Button Unknown" (259), "Button Unknown" (259), "Button Unknown" (259), "Button Unknown" (259)
    Evdev Scrolling Distance (271):    1, 1, 1
    Evdev Middle Button Emulation (272):    0
    Evdev Middle Button Timeout (273):    50
    Evdev Third Button Emulation (274):    0
    Evdev Third Button Emulation Timeout (275):    1000
    Evdev Third Button Emulation Button (276):    3
    Evdev Third Button Emulation Threshold (277):    20
    Evdev Wheel Emulation (278):    0
    Evdev Wheel Emulation Axes (279):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (280):    10
    Evdev Wheel Emulation Timeout (281):    200
    Evdev Wheel Emulation Button (282):    4
    Evdev Drag Lock Buttons (283):    0

```

---

### Post by Autodave on 2017-05-18
Since no one else has jumped in.......and this is coming from a mechanic.......my thought would be to disassemble the mouse and snip one of the wires going to that button. Unless someone else comes to your rescue.......................

---

### Post by eev2 on 2017-05-19
That thought also crossed my mind at one point but I was hoping for a more elegant solution :)

---

### Post by efflandt on 2017-05-19
In a terminal window, what does **xev** show when you press that button? For example my Logitech MX Master has a hidden button on its foot below my thumb, which if accidentally touched in the middle of an online game (even full screen) would drop me into the desktop. Using xev showed me that pressing that button did:```
KeyPress event, serial 37, synthetic NO, window 0x5200001,
    root 0x1da, subw 0x0, time 249436009, (-423,360), root:(779,412),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 37, synthetic NO, window 0x5200001,
    root 0x1da, subw 0x0, time 249436017, (-423,360), root:(779,412),
    state 0x4, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 37, synthetic NO, window 0x5200001,
    root 0x1da, subw 0x0, time 249436025, (-423,360), root:(779,412),
    state 0xc, keycode 23 (keysym 0xff09, Tab), same_screen YES,
    XLookupString gives 1 bytes: (09) "    "
    XmbLookupString gives 1 bytes: (09) "    "
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x5200001,
    root 0x1da, subw 0x0, time 249436033, (-423,360), root:(779,412),
    state 0xc, keycode 23 (keysym 0xff09, Tab), same_screen YES,
    XLookupString gives 1 bytes: (09) "    "
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x5200001,
    root 0x1da, subw 0x0, time 249436041, (-423,360), root:(779,412),
    state 0xc, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x5200001,
    root 0x1da, subw 0x0, time 249436049, (-423,360), root:(779,412),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```In other words Ctrl+Alt+Tab. So with CompizConfig Settings Manager > Ubuntu Unity Plugin > Switcher I found that key combination for switching windows and changed it from Ctrl+Alt+Tab to Ctrl+Alt+Home and Disabled one other thing, so that mouse button no longer does anything. But I can still switch to the desktop even if a full screen program stops responding using Ctrl+Alt+Home.

---

### Post by eev2 on 2017-05-23
Hi efflandt,

Thank you for your reply. In xev I get multiple lines with the following

```
KeyPress event, serial 37, synthetic NO, window 0x6200001,
    root 0xba, subw 0x0, time 1255841, (166,-8), root:(1037,465),
    state 0x10, keycode 180 (keysym 0x1008ff18, XF86HomePage), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x6200001,
    root 0xba, subw 0x0, time 1255891, (166,-8), root:(1037,465),
    state 0x110, keycode 180 (keysym 0x1008ff18, XF86HomePage), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

I did what you advised and removed the keyboard shortcut for [FONT=courier new]XF86HomePage[/FONT]

---

