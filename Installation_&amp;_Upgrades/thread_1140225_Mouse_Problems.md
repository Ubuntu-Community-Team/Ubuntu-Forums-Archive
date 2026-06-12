---
title: "Mouse Problems"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by torgrot on 2009-04-27
I did a fresh install to VMWare.  I did this with 8.10 and had no problems.  I have problems with the scroll wheel under 9.04.  It only scrolls in one direction.

gtgrot@gtgrot-desktop:~$ xinput list
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
"AT Translated Set 2 keyboard"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=3    [XExtensionPointer]
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
"ImPS/2 Generic Wheel Mouse"    id=4    [XExtensionPointer]
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
gtgrot@gtgrot-desktop:~$ 

This is a pretty generic Dell 2 button USB mouse with scroll wheel. Nothing fance.

I just want it to scroll normally like it does in 8.10

---

### Post by torgrot on 2009-04-27
Here is the output in 8.10.  How do I get 9.04 to use the same?
gtgrot@desktop:~$ xinput list
"Virtual core keyboard"    id=0    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Virtual core pointer"    id=1    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is 0
        Max_value is -1
        Resolution is 0
"Macintosh mouse button emulation"    id=2    [XExtensionPointer]
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
"ImPS/2 Generic Wheel Mouse"    id=3    [XExtensionPointer]
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 65535
        Resolution is 10000
    Axis 1 :
        Min_value is 0
        Max_value is 65535
        Resolution is 10000
"AT Translated Set 2 keyboard"    id=4    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255

---

