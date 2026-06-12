---
title: "&quot;End&quot; key recognized as Super_L in xev"
date: 2010-12-23
forum: Hardware
---

### Post by ranjith19 on 2010-12-23
I have a Dell Vostro 1510. I can not use the *End* key when editing. When I use 
[FONT="Courier New"]xev[/FONT] and press the *End* key I get the following output:
[FONT="Courier New"]KeyPress event, serial 29, synthetic NO, window 0x4c00001,
    root 0x15a, subw 0x0, time 10109120, (400,176), root:(404,238),
    state 0x0, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x4c00001,
    root 0x15a, subw 0x0, time 10109189, (400,176), root:(404,238),
    state 0x40, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes:[/FONT]

Home key is working as it is supposed to. No problem with any other key as far as I know. 

The same problem occurs even if I am using an external key board.

---

