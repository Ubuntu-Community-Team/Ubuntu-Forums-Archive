---
title: "Tablet Stylus Way to Sensitive"
date: 2009-12-09
forum: Hardware
---

### Post by dambrown on 2009-12-09
I recently a used, OS-less IBM X41 tablet.  I put Ubuntu Netbook Remix on it.  Input from the stylus is way too sensitive.  When I try to click, 75% of the time, it thinks I'm trying to drag.  I increased the drag-and-drop threshold in the mouse settings, but that did nothing.  is there any way to stabilize the stylus position/make it less sensitive?

---

### Post by Favux on 2009-12-09
Hi dambrown,

Welcome to Ubuntu Forums!

The Thinkpad X41t has a serial Wacom digitizer.  It doesn't sound like you have it working with the linuxwacom drivers.  What is the output in a terminal of:
```
xinput --list
```

---

### Post by dambrown on 2009-12-09
It looks like it is using the Wacom driver.

```
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"ThinkPad Extra Buttons"    id=2    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Wacom Serial Tablet PC Pen Tablet/Digitizer"    id=3    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 24576
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 18432
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"AT Translated Set 2 keyboard"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Sleep Button"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=7    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"    id=8    [XExtensionKeyboard]
    Type is Wacom Eraser
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 24576
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 18432
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"TPPS/2 IBM TrackPoint"    id=9    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Macintosh mouse button emulation"    id=10    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1

```

---

### Post by Favux on 2009-12-09
Hi dambrown,

You are correct.  Make sure in Synaptic Package Manager you have both linuxwacom 0.8.4-1 packages installed:  xserver-xorg-input-wacom & wacom-tools.  I assume you have the Karmic (9.10) version of the Netbook Remix?

Given what HAL is calling your stylus and eraser you won't be able to rotate the tablet or use wacomcpl.  Wacomcpl is the linuxwacom calibration and configuration gui, which might straighten out your problem with the stylus.  Right now:
```
xsetwacom list
```
will be blank instead of returning stylus and eraser.  There are a couple of ways to deal with this.  See [Jaunty (9.04) & Karmic (9.10) Users]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") near the top.  There's some explanations and options.  You might want to try the new rc1 .fdi attached to the bottom of the HOW TO.  The instructions are in Section 2 b).  Setting up wacomcpl is described in Section 3.

Good luck!

---

### Post by dambrown on 2009-12-09
OK, that fixed the stylus for everything except the Netbook Remix launcher.  I can't open anything with the stylus click (except on the Favorites tab), I have to right-click > open.

---

### Post by Favux on 2009-12-09
Hi dambrown,

Great!  I hope you mean you used the new rc1 .fdi and it worked for you.  Yours would be the second confirmation from a serial tablet pc I've gotten.

> except the Netbook Remix launcher. I can't open anything with the stylus click (except on the Favorites tab), I have to right-click > open.

That I don't understand.  If it's behaving as a left mouse click, like it should, why doesn't the Netbook Remix launcher accept that?  Is there a preference somewhere telling it what launch for?  In wacomcpl with stylus in Tool Buttons you have Button1 as left, correct?

---

### Post by dambrown on 2009-12-11
Yeah the fdi made it recognize the stylus no problem.  The netbook launcher just behaves oddly.  I just disabled it and used the regular Gnome menu.

---

