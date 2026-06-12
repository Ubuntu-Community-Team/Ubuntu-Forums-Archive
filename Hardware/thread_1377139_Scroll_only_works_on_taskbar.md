---
title: "Scroll only works on taskbar"
date: 2010-01-09
forum: Hardware
---

### Post by TheCastellum on 2010-01-09
Hello,

My mouse scroll wheel seems to only work on taskbar for switched workspaces/programs, but not in any other programs, such as Firefox, gedit or the terminal. I've done much Googling (which is a pain without scroll), and could only find instances where it worked for nothing at all. I have run xev and it returns the following:
```

LeaveNotify event, serial 30, synthetic NO, window 0x3c00001,
    root 0x102, subw 0x0, time 3903623, (135,103), root:(138,174),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 16

EnterNotify event, serial 30, synthetic NO, window 0x3c00001,
    root 0x102, subw 0x0, time 3903623, (135,103), root:(138,174),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonPress event, serial 30, synthetic NO, window 0x3c00001,
    root 0x102, subw 0x0, time 3903624, (135,103), root:(138,174),
    state 0x10, button 7, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x3c00001,
    root 0x102, subw 0x0, time 3903624, (135,103), root:(138,174),
    state 0x10, button 7, same_screen YES

LeaveNotify event, serial 30, synthetic NO, window 0x3c00001,
    root 0x102, subw 0x0, time 3904759, (135,103), root:(138,174),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 16

EnterNotify event, serial 30, synthetic NO, window 0x3c00001,
    root 0x102, subw 0x0, time 3904759, (135,103), root:(138,174),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonPress event, serial 30, synthetic NO, window 0x3c00001,
    root 0x102, subw 0x0, time 3904760, (135,103), root:(138,174),
    state 0x10, button 6, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x3c00001,
    root 0x102, subw 0x0, time 3904760, (135,103), root:(138,174),
    state 0x10, button 6, same_screen YES

```I am running Ubuntu Desktop 9.10 (Karmic Koala), Any help would be appreciated.

Thank you in advance,
TheCastellum.

Edit: I just found out that my scroll wheel controls my horizontal scroll instead of my vertical scroll.

---

