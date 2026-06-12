---
title: "Mouse problem: scrolling down"
date: 2010-02-09
forum: Hardware
---

### Post by brolzwerver on 2010-02-09
Since 2 days scrolling down is only possible by pressing the scrollwheel (button 2) and then scrolling down. (Scrolling with the touchpad doesn't work either.)
The problem started after upgrading to Ubuntu 9.10 kernel 2.6.31-19-386 (now I'm on kernel 2.6.31-20-386). After each update my graphics don't work, so I have to reinstall the hardware driver (nvidia). Before I install the graphics driver, scrolling down works like it always has; after it's broken. (Both in version 190 & 195, both have been used before without a problem.)

This is what xev gives me when I try to scroll down, the normal way:
```
FocusOut event, serial 36, synthetic NO, window 0x6a00001,
    mode NotifyGrab, detail NotifyNonlinear

EnterNotify event, serial 36, synthetic NO, window 0x6a00001,
    root 0x154, subw 0x0, time 7461096, (125,102), root:(131,159),
    mode NotifyUngrab, detail NotifyNonlinear, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  76  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusIn event, serial 36, synthetic NO, window 0x6a00001,
    mode NotifyUngrab, detail NotifyNonlinear

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  4294967213 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
```
This is what I have to do now:
```
ButtonPress event, serial 36, synthetic NO, window 0x6a00001,
    root 0x154, subw 0x0, time 7574541, (145,134), root:(151,191),
    state 0x0, button 2, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x6a00001,
    root 0x154, subw 0x0, time 7575341, (145,134), root:(151,191),
    state 0x200, button 5, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x6a00001,
    root 0x154, subw 0x0, time 7575341, (145,134), root:(151,191),
    state 0x1200, button 5, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x6a00001,
    root 0x154, subw 0x0, time 7577117, (145,134), root:(151,191),
    state 0x200, button 2, same_screen YES
```
Scrolling up works like before:
```
ButtonPress event, serial 36, synthetic NO, window 0x6a00001,
    root 0x154, subw 0x0, time 7524510, (165,137), root:(171,194),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x6a00001,
    root 0x154, subw 0x0, time 7524510, (165,137), root:(171,194),
    state 0x800, button 4, same_screen YES
```
Output from the touchpad is the same.


xorg.conf hasn't changed. only part about the mouse/touchpad:
```
Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
	# generated from default
EndSection

```

Any tips on getting it to work?
Thanks!

---

### Post by brolzwerver on 2010-02-10
bump

---

### Post by flippo on 2010-02-11
Not that this is addressing the source of your problems by any means, but have you tried removing the section from Xorg and letting hal automatically detect and configure your mouse (if your lucky it may solve your problem)?

---

