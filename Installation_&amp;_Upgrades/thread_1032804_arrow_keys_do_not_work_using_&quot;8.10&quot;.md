---
title: "arrow keys do not work using &quot;8.10&quot;"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by phibuntu on 2009-01-06
Hi all

I have just upgraded to ubuntu "8.10" and tried my _[keyboard layout]("http://www.freimann.eu/eliphi/phi/keyboard")_. 

For the ".Xmodmap" see:
[http://www.freimann.eu/eliphi/phi/keyboard/XKeymap.tgz](http://www.freimann.eu/eliphi/phi/keyboard/XKeymap.tgz)

The ".Xmodmap" worked properly in several linux distributions including all versions of ubuntu before "8.10".

Details: Only the "right arrow key" works. All the special characters using the "window key" as modifier don't work.

I googled some forums including

[http://ubuntuforums.org/showthread.php?t=961322](http://ubuntuforums.org/showthread.php?t=961322)

but even there I have not found any solution. 
Is something wrong in my configuration?

"xev" says that my "window key" has keycode 133.

The arrow keys in the sequence "up" "left" "down" "rigth" cause the following output:


```
KeyPress event, serial 33, synthetic NO, window 0x3800001,
    root 0x71, subw 0x0, time 3664948, (320,-29), root:(483,948),
    state 0x0, keycode 111 (keysym 0xff20, Multi_key), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: True

KeyRelease event, serial 33, synthetic NO, window 0x3800001,
    root 0x71, subw 0x0, time 3665030, (320,-29), root:(483,948),
    state 0x20, keycode 111 (keysym 0xff20, Multi_key), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x3800001,
    root 0x71, subw 0x0, time 3665211, (320,-29), root:(483,948),
    state 0x0, keycode 113 (keysym 0xffea, Alt_R), same_screen YES,
    XKeysymToKeycode returns keycode: 108
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x3800001,
    root 0x71, subw 0x0, time 3665298, (320,-29), root:(483,948),
    state 0x8, keycode 113 (keysym 0xffea, Alt_R), same_screen YES,
    XKeysymToKeycode returns keycode: 108
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x3800001,
    root 0x71, subw 0x0, time 3665427, (320,-29), root:(483,948),
    state 0x0, keycode 116 (keysym 0xff7e, Mode_switch), same_screen YES,
    XKeysymToKeycode returns keycode: 115
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

PropertyNotify event, serial 33, synthetic NO, window 0x3800001,
    atom 0x1ad (XKLAVIER_STATE), time 3665429, state PropertyNewValue

PropertyNotify event, serial 33, synthetic NO, window 0x3800001,
    atom 0x1ad (XKLAVIER_STATE), time 3665430, state PropertyNewValue

KeyRelease event, serial 33, synthetic NO, window 0x3800001,
    root 0x71, subw 0x0, time 3665524, (320,-29), root:(483,948),
    state 0x2000, keycode 116 (keysym 0xff7e, Mode_switch), same_screen YES,
    XKeysymToKeycode returns keycode: 115
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

PropertyNotify event, serial 33, synthetic NO, window 0x3800001,
    atom 0x1ad (XKLAVIER_STATE), time 3665526, state PropertyNewValue

PropertyNotify event, serial 33, synthetic NO, window 0x3800001,
    atom 0x1ad (XKLAVIER_STATE), time 3665527, state PropertyNewValue

KeyPress event, serial 33, synthetic NO, window 0x3800001,
    root 0x71, subw 0x0, time 3665649, (320,-29), root:(483,948),
    state 0x0, keycode 114 (keysym 0xff53, Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: True

KeyRelease event, serial 33, synthetic NO, window 0x3800001,
    root 0x71, subw 0x0, time 3665740, (320,-29), root:(483,948),
    state 0x0, keycode 114 (keysym 0xff53, Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False



```

Any idea?

---

### Post by phibuntu on 2009-01-07
Solved

The Keycodes on "8.04" and "8.10" differ. I had to change the .Xmodmap file to the following and now everything works well.

```
keycode 107  = Delete

! Windows key, left and right
!
!keycode 115 = Super_L

!!!!!!!!!!!!!!!!!!!!!
! kiffi board (phi) !
!!!!!!!!!!!!!!!!!!!!!

!Modifiers
clear Shift
clear Lock
clear Control
clear mod1
clear mod2
clear mod3
clear mod4
clear mod5

!for all keycodes:
!keycode A = A; Shift-A, Mode_Switch-A; Mode_Switch-Shift-A 

! left & right alt and ctrl are treated same:

!Both control keys as symbol "Control" (and Capslock also: 66)
keycode 66 = Control_L
keycode 109 =  Control_R
keycode 37 = Control_L

!both alt keys as symbol (mod1)
keycode 64 = Alt_L
keycode 108 = Alt_R

!Right menu key is meta (as ESC) used for Emacs (mod2)
!keycode 117 = Hyper_R
keycode 117 = Meta_R

!Print screen is treated as Multi_Key (mod 3)
keycode 111 = Multi_key

!Num Lock key as Num_Lock (mod 4)
!keycode 77 = Bare_Num_Lock

!Windows keys as Mode_switch (mod 5)
!keycode 115 = Mode_switch
keycode 133 = Mode_switch
!keycode 116 = Mode_switch

keycode 113 = Left
keycode 114 = Right
keycode 111 = Up
keycode 116 = Down


!PHI Dvorak for german programmers 
!extensions like z and y at different positions.

keycode 10   = 1 0x0021 onesuperior

keycode 11   = 2  at twosuperior
keycode 12   = 3  0x0023 threesuperior
keycode 13   = 4  dollar 
keycode 14   = 5  percent
keycode 15   = 6  0x005E
keycode 16   = 7 ampersand
keycode 17   = 8 asterisk
keycode 18   = 9 parenleft
keycode 19   = 0 parenright
keycode 20 = minus underscore ssharp ssharp
keycode 21   = equal plus

!backspace
!keycode 22   = BackSpace
keycode  22  = BackSpace BackSpace 0xFD1A

!tabulator
keycode 23   = Tab

keycode 24   = q Q
keycode 25   = w W
keycode 26   = h H
keycode 27   = v V
keycode 28   = j J
keycode 29   = z Z
keycode 30   = u U uacute ugrave
keycode 31   = k K
keycode 32   = l L
keycode 33   = p P
keycode 34   = braceleft braceright udiaeresis Udiaeresis
keycode 35   = bracketleft bracketright 

keycode 38 = t T
keycode 39 = s S
keycode 40 = r R
keycode 41 = n N ntilde Ntilde
keycode 42 = g G
keycode 43 = o O oacute ograve
keycode 44 = e E eacute egrave
keycode 45 = i I iacute igrave
keycode 46 = a A aacute agrave

keycode 47 = semicolon colon odiaeresis Odiaeresis
keycode 48 = apostrophe quotedbl adiaeresis Adiaeresis
keycode 49   = 0x0060  0x007E 

keycode 51   = backslash 0x007C 

keycode 52 = y Y
keycode 53 = b B
keycode 54 = c C ccedilla Ccedilla
keycode 55 = d D
keycode 56 = x X
keycode 57 = f F
keycode 58 = m M

keycode 59   = comma 0x003C
keycode 60   = period 0x003E
keycode 61   = slash 0x003F 0x00BF


! META KEYS
add Shift   = Shift_L Shift_R

! caps Lock is now ctrl
! add Lock    = Caps_Lock
add Control = Control_R Control_L
add mod1    = Alt_L Alt_R
add mod2    = Meta_R Meta_L
add mod3    = Multi_key
add mod4    = Num_Lock
add mod5    = Mode_switch
```

---

