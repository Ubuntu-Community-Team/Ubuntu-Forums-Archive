---
title: "Logitech G510 side mouse buttons not working"
date: 2014-01-05
forum: Hardware
---

### Post by kdiab on 2014-01-05
Hi guys,

I recently bought a Logitech M510 mouse.  I'm on 12.04 LTS.   All the buttons work except the forward and back buttons on the side.  I opened xev to see if I could manually bind the buttons using xbindkeys, but when I run xev to figure out which button is which, I get the following from pressing the back and forward buttons in that order:

```

LeaveNotify event, serial 34, synthetic NO, window 0x3200001,
    root 0x100, subw 0x0, time 2015228, (120,160), root:(1401,893),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

EnterNotify event, serial 34, synthetic NO, window 0x3200001,
    root 0x100, subw 0x0, time 2015373, (120,160), root:(1401,893),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

LeaveNotify event, serial 34, synthetic NO, window 0x3200001,
    root 0x100, subw 0x0, time 2017007, (120,160), root:(1401,893),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

EnterNotify event, serial 34, synthetic NO, window 0x3200001,
    root 0x100, subw 0x0, time 2017115, (120,160), root:(1401,893),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  

```
Obviously these are not button presses, but some more complicated events.  What's going on?

---

