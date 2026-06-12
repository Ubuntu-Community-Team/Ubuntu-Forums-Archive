---
title: "Problem with function keys"
date: 2009-07-04
forum: Hardware
---

### Post by luquino on 2009-07-04
Hi to all!
I have Ubuntu 9.04 X86_64, my keyboard has some dedicated keys to start programs:
- Media player  (audacious)
- E-Mail Client (evolution)
- Web Browser   (firefox)
- Calculator    (gcalctool)

plus others for 
- Volume +
- Volume -
- Volume mute
- Power off

In the last 15 days (I can't say exactly when) the keys of the first group have stopped to work, the keys of the second group are still working.
The first trial I made was to check if those keys are sending the right sequence: they are sending it, I checked with gnome-keybinding-properties.
After that I checked in gnome-default-applications-properties if the programs were correctly setted: they were.

I don' t know if any automatic update is responsible for this because for a short while I was on holiday.

Does somebody knows which could be the problem?

---

### Post by cknight on 2009-07-04
Are your keys firing events?  E.g. are they sending notifications to the OS that they've been pressed?  You can easily check this by opening a terminal and running:
```
xev
```
Each key press should result in new output (usually twice, once for press down event and once for release event).

---

### Post by luquino on 2009-07-04
this is the output in xev of the e-mail client key
> FocusOut event, serial 36, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 36, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 36, synthetic NO, window 0x3c00001,
    root 0x13c, subw 0x0, time 9303567, (794,603), root:(802,688),
    state 0x10, keycode 163 (keysym 0x1008ff19, XF86Mail), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False



---

### Post by luquino on 2009-07-05
no more ideas?

---

