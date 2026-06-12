---
title: "Remap headset keys"
date: 2013-05-18
forum: Hardware
---

### Post by rosaage on 2013-05-18
How can I remap my headset keys? my headset is Logitech G930
Looked around and found out I should use xev to get keys, but i get a strange output:

```
MappingNotify event, serial 43, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

FocusOut event, serial 43, synthetic NO, window 0x4a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 44, synthetic NO, window 0x4a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 44, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  

```

When i press my shift key or something like that i get the normal output, but not with the headset keys, and all the 3 keys seems to give the same output.

---

### Post by rosaage on 2013-06-04
Anyone know how to do this?

---

