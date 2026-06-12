---
title: "Has anyone tamed Logitech VX Revolution with a working SEARCH button?"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by jasonxh on 2008-01-03
With evdev, all mouse buttons work wonderfully without much fuss. However I just can't get the search button working, which is supposedly to be recognized as a keyboard event. xev shows a whole bunch of strange messages I can't decipher, e.g.
```
FocusOut event, serial 29, synthetic NO, window 0x4400001,
    mode NotifyGrab, detail NotifyAncestor

EnterNotify event, serial 29, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 12860838, (1,1), root:(9,74),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  89  0   0   0   0   0   0   0   0   0   0   0   0   0   0   4   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

LeaveNotify event, serial 29, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 12860842, (366,434), root:(374,507),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus YES, state 24

EnterNotify event, serial 29, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 12860842, (1,1), root:(9,74),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus YES, state 24

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  89  0   0   0   0   0   0   0   1   0   0   0   0   0   0   4   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

LeaveNotify event, serial 29, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 12860843, (366,434), root:(374,507),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus YES, state 24

EnterNotify event, serial 29, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 12860843, (1,1), root:(9,74),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus YES, state 24

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  89  0   0   0   0   0   0   0   33  0   0   0   0   0   0   4   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

LeaveNotify event, serial 29, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 12860844, (366,434), root:(374,507),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus YES, state 24

EnterNotify event, serial 29, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 12860844, (1,1), root:(9,74),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus YES, state 24

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  89  0   0   0   0   0   0   0   1   0   0   0   0   0   0   4   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

LeaveNotify event, serial 29, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 12860845, (366,434), root:(374,507),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus YES, state 16

FocusIn event, serial 29, synthetic NO, window 0x4400001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 29, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```
and this is just for ONE single click & release of that button... Seems like the real KeyPress event is hijacked by some unknown power. I do remember the first time I plugged this toy in, xev showed regular KeyPress & KeyRelease events for the search button, with keycode 122. I've already tried reverting every single modification I made, as far as I can remember, but still no go. I'm like mad now :mad:

Just wonder if anyone has successful experience with it?

---

### Post by jasonxh on 2008-01-03
Please ignore this post. I hijacked the key myself, in metacity global keybindings! :)

---

