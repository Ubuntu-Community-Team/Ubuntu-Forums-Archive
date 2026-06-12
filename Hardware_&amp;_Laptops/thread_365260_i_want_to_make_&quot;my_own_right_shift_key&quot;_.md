---
title: "i want to make &quot;my own right shift key&quot; :) plz help"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by fabjin on 2007-02-19
the right shift key of my laptop is mapped inconveniently,
so i want to make some NoSymbol key to be right shift.

however, after remapping keys, the "new right shift key" doesn't work.
that's because the new one does KeyPress and KeyRelease simultaneously.

remove Shift = Shift_R
keycode 211 = Shift_R
keycode 62 = NoSymbol
add Shift = Shift_R

this is my .Xmodmap, keycode 211 is the new one i want to use,
keycode 62 is default right shift key.

jin@ubuntu:~$ xmodmap
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0xd3)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        Mode_switch (0x5d),  ISO_Level3_Shift (0x71),  ISO_Level3_Shift (0x7c)

Shift_R (0xd3) is the new one, remapped successfully.

by the way, it doesnt work, so i confirmed with 'xev' and i found the problem

KeyPress event, serial 26, synthetic NO, window 0x2e00001,
    root 0x45, subw 0x0, time 3669974751, (170,711), root:(175,759),
    state 0x0, keycode 211 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 26, synthetic NO, window 0x2e00001,
    root 0x45, subw 0x0, time 3669974751, (170,711), root:(175,759),
    state 0x1, keycode 211 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 29, synthetic NO, window 0x2e00001,
    root 0x45, subw 0x0, time 3669976026, (170,711), root:(175,759),
    state 0x0, keycode 62 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2e00001,
    root 0x45, subw 0x0, time 3669976149, (170,711), root:(175,759),
    state 0x0, keycode 62 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


the first is new right shift key, and the second is default one.

plz help me.

how could i use my own right shift key?

thank you.

---

