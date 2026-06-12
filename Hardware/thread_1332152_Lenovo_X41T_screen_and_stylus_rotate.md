---
title: "Lenovo X41T screen and stylus rotate"
date: 2009-11-20
forum: Hardware
---

### Post by Temetka on 2009-11-20
Hi guys,

I've spent the last few days trying to screen and stylus rotation to work on my X41T under Ubuntu 9.10. I did load 9.04 and had it working just fine using this page:

[http://www.linux.com/community/blogs/installing-ubuntu-904-on-a-ibm-x41-tablet.html](http://www.linux.com/community/blogs/installing-ubuntu-904-on-a-ibm-x41-tablet.html)

Under 9.10 the main 'rotatetablet' works fine. However the stylus does not rotate.

I have been all over the internet, read linken's page, read I don't know how many pages of supposed tips and tricks to get stylus rotation to work on this machine. My head is spinning with various .fdi files, scripts, rc.d updates and so on. 

As an end user all I want is this:

1. I do NOT want auto rotation because sometimes I use the tablet in landscape mode.

Ideally I want to create 2 buttons on my gnome launchbar:

Button 1: Rotate the screen 90 degrees right and rotate the stylus 90 degrees right
Button 2: Rotate the screen 90 degrees left and rotate the stylus 90 degrees left.

I do have wacom tools installed.

If someone could please, please, please help me cook up 2 scripts to do what I want I would be extemely grateful. I usually figure myself to be a good linux user as I have set up RHEL servers in the past, Asterisk boxes and so on. This screen rotation thing is just breaking me.

Any help in resolving this in as simple a manner as possible would be greatly appreciated.

Thank you.

Here is the output of xinput --list to get things going:

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

### Post by Favux on 2009-11-20
Hi Temetka,

Hal/dbus is calling:

stylus = "Wacom Serial Tablet PC Pen Tablet/Digitizer"

eraser = "Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"

The xsetwacom rotate commands and wacomcpl won't work until:
```
xsetwacom list
```
returns stylus and eraser.  In other words the default linuxwacom.fdi is not parsing the names correctly into linuxwacom names.  Or you can rename things.

See "Jaunty (9.04) & Karmic (9.10) Users" at this [HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") near the top, esp. 3) an 3a) and 5).  Also attached to the bottom of the HOW TO is a new serial linuxwacom.fdi that I believe will parse the names correctly.

---

### Post by Temetka on 2009-11-20
To be honest this is way too much work for me.

I've already started to reload Windows on this machine.

Thanks for your help anyway.

Perhaps I will attempt Linux again on my tablet when the dev's can get it to work OOTB.

---

### Post by Favux on 2009-11-20
Hi Temetka,

Too bad.  It isn't that much work.  There's only a few steps.  It might look a little daunting because I have explanations in there, rather than just a few commands without explanations.

---

