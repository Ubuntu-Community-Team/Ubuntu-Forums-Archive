---
title: "Volume FN-Buttons problem - Vaio SZ2HP"
date: 2008-10-29
forum: Hardware
---

### Post by gdev on 2008-10-29
Hi,

I got Ubuntu running without any problems for about 5 months now. All the volume and brightness buttons worked fine.

But since last week, I can't use the volume keys (FN+F2, FN+F3, FN+F4) anymore. Every time I try to change the volume by pressing these keys, the volume changes two times - so if I try to mute my  notebook the result ist a quick change like "mute - loud"

With xev I got the following results:
```
KeyPress event, serial 31, synthetic NO, window 0x3c00001,
    root 0x5e, subw 0x0, time 5157459, (193,-146), root:(199,314),
    state 0x0, keycode 101 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3c00001,
    root 0x5e, subw 0x0, time 5157471, (193,-146), root:(199,314),
    state 0x0, keycode 101 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```
This is the output after pressing the brightness key ONE time (seems to be quite okay) and pressing ONE time the Mute Button.

Can aynbody help me?
Greetings, Gdev

(Ubuntu Hardy Heron 8.04.1, Sony Vaio VGN-SZ2HP/B)

---

