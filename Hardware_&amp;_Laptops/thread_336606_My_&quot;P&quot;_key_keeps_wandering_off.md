---
title: "My &quot;P&quot; key keeps wandering off"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by jsteve54302 on 2007-01-11
Hey, here's a strange one...  Whenever  I leave my computer unattended for a while, my "P" key wanders off (i.e., pressing it does nothing).  I can call it back and corral it for a while by changing my keyboard layout in System->Preferences->Keyboard, but it always wanders off again when I leave my computer alone for a while.  This may happen with other keys, but I haven't noticed it if it does.  This seems to have started after an unsuccessful resume from hibernation in ubuntu, and happens with all 3 of the keyboards I've tested.  BTW, this did happen once in XP, after an unsuccessful resume from hibernation there, but it fixed itself after disabling usb keyboard support in the BIOS.

Since I BOINC, this is very annoying.  Anybody have any ideas, or better, solutions?

TIA,

---

### Post by jsteve54302 on 2007-01-14
UDATE:  I figured out the roblem...  the XF86Audioause has been maed to the "" key, and there are no GUI utils witch will let me fix it...  lease, i beg you, can somebody oint in the directsio of the keyma file I need to edit to fix this roblem?!  Once I know where the scancode-to-keyress mafile is i should be able to find the right maing entry...  I just can't find the right file ](*,)](*,):(

---

### Post by jsteve54302 on 2007-01-14
Sorry...  Another udate...  I,ve now tried 3 keyboards, 2 S/2 and 1 USB...  Same thing with all of them...  ressing "o[" gives the following outut in xev:
```
KeyPress event, serial 32, synthetic NO, window 0x3600001,
    root 0x1a5, subw 0x0, time 578119724, (178,84), root:(1530,896),
    state 0x10, keycode 32 (keysym 0x6f, o), same_screen YES,
    XLookupString gives 1 bytes: (6f) "o"
    XmbLookupString gives 1 bytes: (6f) "o"
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x3600001,
    root 0x1a5, subw 0x0, time 578119804, (178,84), root:(1530,896),
    state 0x10, keycode 32 (keysym 0x6f, o), same_screen YES,
    XLookupString gives 1 bytes: (6f) "o"
    XFilterEvent returns: False

FocusOut event, serial 32, synthetic NO, window 0x3600001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 32, synthetic NO, window 0x3600001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 32, synthetic NO, window 0x3600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 32, synthetic NO, window 0x3600001,
    atom 0xf2 (_NET_WM_STATE), time 578120669, state PropertyNewValue

KeyPress event, serial 32, synthetic NO, window 0x3600001,
    root 0x1a5, subw 0x0, time 578122396, (178,84), root:(1530,896),
    state 0x10, keycode 34 (keysym 0x5b, bracketleft), same_screen YES,
    XLookupString gives 1 bytes: (5b) "["
    XmbLookupString gives 1 bytes: (5b) "["
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x3600001,
    root 0x1a5, subw 0x0, time 578122468, (178,84), root:(1530,896),
    state 0x10, keycode 34 (keysym 0x5b, bracketleft), same_screen YES,
    XLookupString gives 1 bytes: (5b) "["
    XFilterEvent returns: False
```



The KeymaNotify and roertyNotify events seem to be the only ones relevent to the key roblem...  Don't know where the FocusIFocusOut came from...

S: See how annoying this is??!

---

### Post by jsteve54302 on 2007-02-10
Eh, never mind...  xmms-XF86Keys was getting confused and grabbing the wrong key...  and I've been mostly using kubuntu anyway...

---

