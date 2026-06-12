---
title: "Cherry CyMotion Master Linux special keys"
date: 2010-12-21
forum: Hardware
---

### Post by M4rv1n on 2010-12-21
Hi!
I have a Cherry CyMotion Master Linux keyboard ps2 connected on lucid 64 bit. Unfortunately keytouch doesn't work any more on my system so I'm playing with xmodmap. In the keyboard property I've set my model of keyboard and every multimedia keys works, except the 10 keys on the extreme left and right of the keyboard. So, following the guide on the wiki, I've open a real terminal and with dmesg I found the keycode of, for example, the launch1 key. This is my rc.local

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

setkeycodes e071 195 # Launch1
exit 0

```So I'm trying to map launch1 key on keycode 195 that is free in xmodmap -pk and also with dumpkeys. After I'd like to associate keycode 195 with XF86Launch1 keysym so I can made a shortcut for that key. This is my .Xmodmap file

```
keysym Super_R = at
keycode 64 = Alt_L
keycode 108 = ISO_Level3_Shift
clear mod1
add mod1 = Alt_L
clear mod5
add mod5 = ISO_Level3_Shift
keycode 195 = XF86Launch1 NoSymbol XF86Launch1
```Now if I open xev and press the launch1 key I aspect to see an event associated with 195 keycode ..... this is the output of xev pressing launch1 key

```
KeyPress event, serial 36, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 941890, (-727,351), root:(596,404),
    state 0x10, **keycode 203 (keysym 0xff7e, Mode_switch)**, same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

PropertyNotify event, serial 36, synthetic NO, window 0x4c00001,
    atom 0x17f (XKLAVIER_STATE), time 941890, state PropertyNewValue

PropertyNotify event, serial 36, synthetic NO, window 0x4c00001,
    atom 0x17f (XKLAVIER_STATE), time 941891, state PropertyNewValue

PropertyNotify event, serial 36, synthetic NO, window 0x4c00001,
    atom 0x17f (XKLAVIER_STATE), time 941891, state PropertyNewValue

PropertyNotify event, serial 36, synthetic NO, window 0x4c00001,
    atom 0x17f (XKLAVIER_STATE), time 941891, state PropertyNewValue

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0x15d, subw 0x0, time 941969, (-727,351), root:(596,404),
    state 0x2010, **keycode 203 (keysym 0xff7e, Mode_switch)**, same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

PropertyNotify event, serial 36, synthetic NO, window 0x4c00001,
    atom 0x17f (XKLAVIER_STATE), time 941970, state PropertyNewValue

PropertyNotify event, serial 36, synthetic NO, window 0x4c00001,
    atom 0x17f (XKLAVIER_STATE), time 941970, state PropertyNewValue

PropertyNotify event, serial 36, synthetic NO, window 0x4c00001,
    atom 0x17f (XKLAVIER_STATE), time 941970, state PropertyNewValue

PropertyNotify event, serial 36, synthetic NO, window 0x4c00001,
    atom 0x17f (XKLAVIER_STATE), time 941970, state PropertyNewValue

```The xev report key 203 pressed associated with switch mode!!!!

:-k where is the error?

---

### Post by M4rv1n on 2010-12-22
:-\" Bump! :-P

---

### Post by Ceyx on 2011-02-06
Why not just change keycode 195 to 203 ?

---

