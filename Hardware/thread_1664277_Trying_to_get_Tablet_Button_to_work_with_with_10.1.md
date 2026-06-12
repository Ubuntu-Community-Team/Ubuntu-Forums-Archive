---
title: "Trying to get Tablet Button to work with with 10.10"
date: 2011-01-10
forum: Hardware
---

### Post by bradyboo222 on 2011-01-10
I am trying to get a tablet button to work. I have tried following a number of different Howtos but none of them have worked.

I have a ThinkPad X61 Tablet and there is a small unlabeled button on the screen that doesn't work. 

I used xev and it output the following:

```
KeyPress event, serial 36, synthetic NO, window 0x3e00001,
    root 0xaa, subw 0x3e00002, time 61152697, (15,42), root:(760,148),
    state 0x0, keycode 128 (keysym 0x1008ff4a, XF86LaunchA), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

"sudo showkey -s" outputs:
0xe0 0x0b   <----- When PRESSED
0xe0 0x8b   <----- When RELEASED

I want the button to behave as the "super" or "windows" button. Or perhaps behave as a key combination like ATL+SUPER.

Help!

---

