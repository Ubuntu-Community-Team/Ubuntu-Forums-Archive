---
title: "Mouse DELL WM524 side buttons don't work"
date: 2016-02-10
forum: Hardware
---

### Post by panico-n1 on 2016-02-10
Hi guys,
at work i have received a Dell Vostro 15 series 3000, and i bought for it a mouse Dell WM524 (bluetooth).
The connection between devices had works immidiatly and my ubuntu 15.10 reconaize all informations about mouse model, charge level, accuracy, etc... but the side buttons do not work in the navigation (forward, back).

For understand the problem, i did this :

```

$ xinput --list-props "Dell Travel Mouse WM524"
Device 'Dell Travel Mouse WM524':
    Device Enabled (139):    1
    Coordinate Transformation Matrix (141):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (269):    0
    Device Accel Constant Deceleration (270):    1.000000
    Device Accel Adaptive Deceleration (271):    1.000000
    Device Accel Velocity Scaling (272):    10.000000
    Device Product ID (259):    1133, 45070
    Device Node (260):    "/dev/input/event16"
    Evdev Axis Inversion (273):    0, 0
    Evdev Axes Swap (275):    0
    Axis Labels (276):    "Rel X" (149), "Rel Y" (150), "Rel Horiz Wheel" (266), "Rel Vert Wheel" (268)
    Button Labels (277):    "Button Left" (142), "Button Middle" (143), "Button Right" (144), "Button Wheel Up" (145), "Button Wheel Down" (146), "Button Horiz Wheel Left" (147), "Button Horiz Wheel Right" (148), "Button Side" (264), "Button Extra" (265), "Button Forward" (619), "Button Back" (620), "Button Task" (621), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262)
    Evdev Scrolling Distance (278):    1, 1, 1
    Evdev Middle Button Emulation (279):    0
    Evdev Middle Button Timeout (280):    50
    Evdev Third Button Emulation (281):    0
    Evdev Third Button Emulation Timeout (282):    1000
    Evdev Third Button Emulation Button (283):    3
    Evdev Third Button Emulation Threshold (284):    20
    Evdev Wheel Emulation (285):    0
    Evdev Wheel Emulation Axes (286):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (287):    10
    Evdev Wheel Emulation Timeout (288):    200
    Evdev Wheel Emulation Button (289):    4
    Evdev Drag Lock Buttons (290):    0

```
In the button labels i saw that there are a lot of buttons (much more than what I expected ) and 4 of these labels are Unknown...
So, i try to understand what buttons are really set to the system with this command :
```

$ xev | grep ', button'
    state 0x10, button 1, same_screen YES
    state 0x110, button 1, same_screen YES
    state 0x10, button 2, same_screen YES
    state 0x210, button 2, same_screen YES
    state 0x10, button 3, same_screen YES
    state 0x410, button 3, same_screen YES
    state 0x10, button 4, same_screen YES
    state 0x810, button 4, same_screen YES
    state 0x10, button 5, same_screen YES
    state 0x1010, button 5, same_screen YES
    state 0x10, button 6, same_screen YES
    state 0x10, button 6, same_screen YES
    state 0x10, button 7, same_screen YES
    state 0x10, button 7, same_screen YES

```
Button 1 = Left button
Button 2 = Wheel press
Button 3 = Right button
Button 4 = Wheel up
Button 5 = Wheel down
Button 6 = Wheel left
Button 7 = Wheel right


When i press the side buttons at Event Viewer of xev command nothing happens.

Someone have a idea what i can do for activate the navigation with my side buttons?

Thank you

---

### Post by panico-n1 on 2016-02-11
Only for knowledge :

since the system cannot receiver any imput from the side buttons, i have used a workaround with xbindkeys, setting mouse button 6 and 7 (Wheel to left/right) like this :
```

$ xbindkeys --default > $HOME/.xbindkeys

```
And add to end file this lines :
```

# Back
"xte 'keydown Alt_L' 'key Left' 'keyup Alt_L'"
  b:6

# Forward
"xte 'keydown Alt_L' 'key Right' 'keyup Alt_L'"
  b:7

```

It's a sad workaround because 2 mouse button are unused by the system, but i can navigate forward and back in browser and in file manager .


Bye

---

### Post by bwanaaa on 2016-02-13
I found that xte is flakey.
My sequence for mapping the the thumb button of my logitech 518 to 'control W' to close tabs and windows never worked well with xte not sequencing properly.
For example this failed:
```
"xte 'keydown Control_L' 'w' 'keyup Control_L'"
 b:8
```

as did this:
```
"xte 'keydown Control_L' 'w' 'keyup Control_L'"
 b:8 + release
```

I also noticed that xte was SLOOOW.
I tried xvkbd and it works well.

OF course you have to get xvkbd with this:
```
sudo apt-get install xvkbd
```

Put this in your .xbindkeysrc file in your home directory
```

"xvkbd  -text '\C\[w]'"
m:0x0 + b:8
```


and restart xbindkeys
pkill -f xbindkeys  && xbindkeys

---

### Post by kodurchaitanya on 2016-10-09
This answer is specifically for "DELL WM524 Bluetooth mouse". One of the side buttons+ "Wheel Left" is equivalent to "ALT+left arrow key" & one of the side buttons+ "Wheel Right" is equivalent to "ALT+Right arrow key". So they can be used by default without a need to configure anything as navigation keys. They also get detected as Button 8 and Button 9 respectively in xev.

---

