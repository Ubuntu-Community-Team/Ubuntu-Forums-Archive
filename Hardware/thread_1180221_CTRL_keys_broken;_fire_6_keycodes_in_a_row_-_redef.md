---
title: "CTRL keys broken; fire 6 keycodes in a row - redefine?"
date: 2009-06-06
forum: Hardware
---

### Post by rumburak on 2009-06-06
Yesterday my notebook accidentally experienced an electric shock. My keyboard went dead, but the mouse did it's work anyway. I finished the session and rebooted. In the new session I experienced that both CTRL keys behaved absolute insane. I add the output by showkey and xev to explain.

```

showkey -s
#CTRL_L:
XC^[B0xe0 0x5b 0x2a 0x2d 0x2e 0x38 0x30 0xe0 0xdb 0xaa 0xad 0xae 0xb8 0xb0
#CTRL_R:
<YF&#294;0x56 0x36 0x2c 0x21 0xe0 0x38 0x23 0xd6 0xb6 0xac 0xa1 0xe0 0xb8 0xa3

```

```

xev
#CTRL_L
KeyPress event, serial 31, synthetic NO, window 0x3400001,
    root 0x7a, subw 0x0, time 74101628, (-24,320), root:(451,347),
    state 0x0, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes:                                     
    XmbLookupString gives 0 bytes:                                   
    XFilterEvent returns: False                                      

KeyPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x7a, subw 0x0, time 74101633, (-24,320), root:(451,347),
    state 0x40, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes:                                     
    XmbLookupString gives 0 bytes:                                   
    XFilterEvent returns: False                                      

KeyPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x7a, subw 0x0, time 74101638, (-24,320), root:(451,347),
    state 0x41, keycode 53 (keysym 0x58, X), same_screen YES,     
    XLookupString gives 1 bytes: (58) "X"                         
    XmbLookupString gives 1 bytes: (58) "X"                       
    XFilterEvent returns: False                                   

KeyPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x7a, subw 0x0, time 74101643, (-24,320), root:(451,347),
    state 0x41, keycode 54 (keysym 0x43, C), same_screen YES,     
    XLookupString gives 1 bytes: (43) "C"                         
    XmbLookupString gives 1 bytes: (43) "C"                       
    XFilterEvent returns: False                                   

KeyPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x7a, subw 0x0, time 74101649, (-24,320), root:(451,347),
    state 0x41, keycode 64 (keysym 0xffe7, Meta_L), same_screen YES,
    XLookupString gives 0 bytes:                                    
    XmbLookupString gives 0 bytes:                                  
    XFilterEvent returns: False                                     

KeyPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x7a, subw 0x0, time 74101654, (-24,320), root:(451,347),
    state 0x49, keycode 56 (keysym 0x42, B), same_screen YES,     
    XLookupString gives 1 bytes: (42) "B"                         
    XmbLookupString gives 1 bytes: (42) "B"                       
    XFilterEvent returns: False
#key release events omitted
#the output for CTRL_R looks similar

```
Can please anyone tell me what happened and how can I fix this?

---

### Post by rumburak on 2009-06-07
Maybe I have to add that I already tried to reassign Control_R and Control_L, respectively to some other keycodes but without any effect. Anyhow, everything seems to be okay as xmodmap suggests:

```

xmodmap
#..
control     Control_L (0x25),  Control_R (0x69)

```

Likewise, the layout for my pc105 keyboards seems to be okay, too:
```

cat /usr/share/X11/xkb/symbols/pc
#..
key <LCTL> {        [ Control_L     ]       };

key <LWIN> {        [ Super_L                       ]       };

key <RTSH> {        [ Shift_R       ]       };
key <RCTL> {        [ Control_R     ]       };
#..

```

I just don't know what went wrong and where and how to help this.

Any ideas left?

---

### Post by rumburak on 2009-06-08
Okay. An external USB keyboard does the trick, so it seems my keyboard controller is broken. There's no help.

---

