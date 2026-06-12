---
title: "LowercaSe S not working properly."
date: 2016-01-30
forum: Hardware
---

### Post by Doesnt_Matter on 2016-01-30
So i inStalled Ubuntu a week ago and at firSt everything worked fine. But after a couple of dayS my lowercaSe S Stopped working. Everywhere. ItS not a hardwareproblem Since i can type uppercaSe S and xev noticeS when i preSS it. Ive done Some reSearch and found out the xev ouput for the key iS really weird. I think it handleS my S key a a functionkey of Some Sort?

FocusOut event, serial 37, synthetic NO, window 0x2e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 37, synthetic NO, window 0x2e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 37, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 

What Should i do? 

ThiS iS a normal key output:

KeyPress event, serial 37, synthetic NO, window 0x2e00001,
    root 0x9f, subw 0x0, time 2913446, (358,378), root: (1229,823),
    state 0x0, keycode 40 (keysym 0x64, d), same_screen YES,
    XLookupString gives 1 bytes: (64) "d"
    XmbLookupString gives 1 bytes: (64) "d"
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x2e00001,
    root 0x9f, subw 0x0, time 2913550, (358,378), root: (1229,823),
    state 0x0, keycode 40 (keysym 0x64, d), same_screen YES,
    XLookupString gives 1 bytes: (64) "d"
    XFilterEvent returns: False

ThankS!

---

