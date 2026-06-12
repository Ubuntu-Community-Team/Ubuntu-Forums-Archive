---
title: "keyboard?"
date: 2009-12-24
forum: Hardware
---

### Post by rosswmcgee on 2009-12-24
I purchased a lighted keyboard, on the net. 

Black LED Lighted Keyboard W-9868BK USB


The scroll lock key is the key that turns the back light on/off. Num light works/caps light works, but the scroll lock light does not on F12 or Ubuntu Thinking it may be a soft ware problem after trying different usb slots, I dug out an old XP machine and it works. 

Is there an answer here or must I return it?

Feel lonesome on Christmas Eve? Do a good deed and figure this out! lol

---

### Post by Fir3chi3f on 2009-12-24
Did the keyboard come with install disks for windows? I don't see why else it would work under windows and not ubuntu.

---

### Post by rosswmcgee on 2009-12-24
No disks just keyboard and usb connection. I am surprised at this myself, never had the problem before.

---

### Post by tgalati4 on 2009-12-24
Open a terminal and run xev.

Output the response of the non-working keys.

---

### Post by rosswmcgee on 2009-12-24
rosswmcgee@rosswmcgee-desktop:~$ xev
Outer window is 0x3a00001, inner window is 0x3a00002

PropertyNotify event, serial 8, synthetic NO, window 0x3a00001,
    atom 0x27 (WM_NAME), time 61643, state PropertyNewValue

PropertyNotify event, serial 9, synthetic NO, window 0x3a00001,
    atom 0x22 (WM_COMMAND), time 61643, state PropertyNewValue

PropertyNotify event, serial 10, synthetic NO, window 0x3a00001,
    atom 0x28 (WM_NORMAL_HINTS), time 61643, state PropertyNewValue

CreateNotify event, serial 11, synthetic NO, window 0x3a00001,
    parent 0x3a00001, window 0x3a00002, (10,10), width 50, height 50
border_width 4, override NO

PropertyNotify event, serial 14, synthetic NO, window 0x3a00001,
    atom 0xee (WM_PROTOCOLS), time 61644, state PropertyNewValue

MapNotify event, serial 15, synthetic NO, window 0x3a00001,
    event 0x3a00001, window 0x3a00002, override NO

ConfigureNotify event, serial 18, synthetic NO, window 0x3a00001,
    event 0x3a00001, window 0x3a00001, (0,0), width 178, height 178,
    border_width 0, above 0x3800001, override NO

PropertyNotify event, serial 18, synthetic NO, window 0x3a00001,
    atom 0x146 (_NET_WM_ALLOWED_ACTIONS), time 61644, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x3a00001,
    atom 0x146 (_NET_WM_ALLOWED_ACTIONS), time 61644, state PropertyNewValue

ReparentNotify event, serial 18, synthetic NO, window 0x3a00001,
    event 0x3a00001, window 0x3a00001, parent 0x1a002b0,
    (0,0), override NO

PropertyNotify event, serial 18, synthetic NO, window 0x3a00001,
    atom 0xf6 (_NET_WM_DESKTOP), time 61644, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x3a00001,
    atom 0xf6 (_NET_WM_DESKTOP), time 61644, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x3a00001,
    atom 0xf3 (_NET_FRAME_EXTENTS), time 61645, state PropertyNewValue

ConfigureNotify event, serial 18, synthetic NO, window 0x3a00001,
    event 0x3a00001, window 0x3a00001, (3,23), width 178, height 178,
    border_width 0, above 0x0, override NO

PropertyNotify event, serial 18, synthetic NO, window 0x3a00001,
    atom 0x11f (WM_STATE), time 61645, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x3a00001,
    atom 0xfc (_NET_WM_STATE), time 61645, state PropertyNewValue

ConfigureNotify event, serial 28, synthetic YES, window 0x3a00001,
    event 0x3a00001, window 0x3a00001, (86,59), width 178, height 178,
    border_width 2, above 0x0, override NO

MapNotify event, serial 28, synthetic NO, window 0x3a00001,
    event 0x3a00001, window 0x3a00001, override NO

VisibilityNotify event, serial 28, synthetic NO, window 0x3a00001,

---

### Post by tgalati4 on 2009-12-29
I don't see any key presses.  You normally get a Key_Press event and a Key_Release event for each key.  Also, the mouse pointer needs to be in the same window as the terminal where you are pressing the keys.

If you don't get any events when you press the problem keys, then you need to set up some keys using the setkeys command.

---

### Post by rosswmcgee on 2009-12-30
I returned it. Still wondering what backlit keyboard to get. I am interested in the 

Logsys 2 color keyboard featured on this page but have not heard from them as to whether it works on linux? This one does but is not back lit just illuminated.
Logisys Streamline Illuminated Keyboard USB / PS2 - Black

---

