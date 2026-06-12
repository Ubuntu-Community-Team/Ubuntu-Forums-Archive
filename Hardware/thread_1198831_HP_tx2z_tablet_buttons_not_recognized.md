---
title: "HP tx2z tablet buttons not recognized"
date: 2009-06-27
forum: Hardware
---

### Post by dandc87 on 2009-06-27
I got my HP tx2z tablet a couple days ago and of course installed Linux Mint 7 (Ubuntu 9.04 basically) on it. I have the stylus and rotation working, but there are three buttons on the side of the screen that are not being recognized.

I've tried a few searching for help, but I can't find any. When I press any of the 3 buttons, nothing happens. Its doesn't show up in **Keyboard Shortcuts** settings, and I don't think it is even being picked up by **x.org**.

Here is the print out of: **xinput list**
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
"stylus"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 9600
        Resolution is 1016
    Axis 1 :
        Min_value is 0
        Max_value is 7200
        Resolution is 1016
    Axis 2 :
        Min_value is 0
        Max_value is 256
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
"touch"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 9600
        Resolution is 0
    Axis 1 :
        Min_value is 0
        Max_value is 7200
        Resolution is 0
    Axis 2 :
        Min_value is 0
        Max_value is 256
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
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=5    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=6    [XExtensionPointer]
    Num_buttons is 32
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
"SynPS/2 Synaptics TouchPad"    id=7    [XExtensionPointer]
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1
"HID 1b96:0001"    id=8    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 9600
        Resolution is 10000
    Axis 1 :
        Min_value is 0
        Max_value is 7200
        Resolution is 10000
"HID 1b96:0001"    id=9    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 5
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 9600
        Resolution is 1016
    Axis 1 :
        Min_value is 0
        Max_value is 7200
        Resolution is 1016
    Axis 2 :
        Min_value is 0
        Max_value is 256
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

```Please help me, I would really like to utilize these buttons.

---

### Post by Favux on 2009-06-28
Hi dandc87,

I don't think anyone's figured out how to get the buttons yet.  The TX2000 (& TX2500) had 2/4 bezel buttons in Hardy.  We lost one in Intrepid.  So we used a trick (described in the Keycode Addendum) and stopped the hotkey-setup daemon and broke it's symlinks and then restarted it.  That got the button back again.  But I don't think it works for Jaunty.

Basically the technique for button mapping is to enter xev in a terminal.  A gui pops up and you press the button and a keycode appears.  But these buttons don't return anything in xev.  I've tried some other things too but no luck.

My guess is that the "missing" bezel buttons signal is going to the HP-WMI kernel module like the swivel hinge.

All this is discussed in a little more detail here:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)

---

