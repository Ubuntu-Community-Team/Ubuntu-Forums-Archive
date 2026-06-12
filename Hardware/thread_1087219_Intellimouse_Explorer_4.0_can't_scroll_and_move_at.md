---
title: "Intellimouse Explorer 4.0 can't scroll and move at same time"
date: 2009-03-04
forum: Hardware
---

### Post by alfredska on 2009-03-04
Device: Microsoft Intellimouse Explorer 4.0 - USB laser mouse with two side buttons and horizontal scrolling capability
Ubuntu: 8.10 with all updates as of 3/18/09, no backports or pre-releases

When I try to use the scroll wheel, the mouse has to be perfectly still for scrolling to function (ie. any slight movement of the mouse cursor stops scrolling).  You might think this is no big deal, but I promise you, when you're scrolling a mouse wheel, more often than not the mouse cursor is making slight movements.

The wheel functions correctly in Vista while the mouse cursor is moving, so this does not seem to be a hardware problem.

Advice?

---

### Post by alfredska on 2009-03-10
Just one bump to let people know that I haven't forgotten about my inquiry.  Is anyone else experiencing this problem with the same (or a similar) mouse?

---

### Post by alfredska on 2009-03-19
Another week has passed.  I'm still hopeful someone has a suggestion about how to fix this problem.

To add another detail, I monitored the output from "xev".  When the mouse is moving there are plenty of MotionNotify events, but if I try to simultaneously scroll the wheel, no ButtonPress/ButtonRelease events occur.  If the mouse is still, the wheel does record ButtonPress/ButtonRelease.

Movement:
```
MotionNotify event, serial 31, synthetic NO, window 0x3a00001,
    root 0x13b, subw 0x0, time 1558428, (92,156), root:(766,207),
    state 0x10, is_hint 0, same_screen YES

```

Wheel without any mouse movement:
```
ButtonPress event, serial 31, synthetic NO, window 0x3a00001,
    root 0x13b, subw 0x0, time 1597004, (62,177), root:(736,228),
    state 0x10, button 5, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x3a00001,
    root 0x13b, subw 0x0, time 1597004, (62,177), root:(736,228),
    state 0x1010, button 5, same_screen YES

```

---

### Post by alfredska on 2009-03-28
This problem persists in Ubuntu 9.04 Beta with all updates as of Mar 28, 2009.

---

