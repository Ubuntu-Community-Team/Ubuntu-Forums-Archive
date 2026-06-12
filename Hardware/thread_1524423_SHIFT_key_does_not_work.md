---
title: "SHIFT key does not work"
date: 2010-07-05
forum: Hardware
---

### Post by kvalis on 2010-07-05
Shift key does not work in Ubuntu, but works in Windows 7.

I presume that if it is used as a shortcut key, it will loose it's normal function!!??

I have gone through the shortcuts, but can not find anywhere that the shift key only is bound to any shortcut.

Is there a way of finding out with a simple command if it is bound up as a shortcut key??

Any help will be appreciated

Tore

---

### Post by Revolutionary101 on 2010-07-05
I noticed that you live in Norway and it may be possible that you have a different keyboard than the default USA keyboard.

Make sure you have the Norway keyboard layout selected in System>Preferences>Keyboard. Then check in the Layout tab to see what keyboard layout you have installed.

---

### Post by drs305 on 2010-07-05
You can also tell how the key is currently mapped by running "xev". Entering "xev" in a terminal will produce a small box. Place the cursor in the box and whatever key you press will provide information about the key, showing it's current assignment. Note that this shows the  physical  key assignment. If a shortcut is tied to this key, it will still display "Shift_L". You can use the following to determine if the output of the key is the result of an assigned shortcut or not.

For instance, once *xev* is opened, with the cursor in the box pressing the SHIFT key produces the following output:
> 
[noparse]KeyRelease event, serial 33, synthetic NO, window 0x4c00001,
    root 0x166, subw 0x0, time 5569269, (243,85), root:(247,212),
    **state 0x11, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,**
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False[/noparse]

If you want to see all the current key assignments, type:
```
xmodmap -pke
```

If you need to reset the key value, you can run this command for the left SHIFT key. It will only keep the assignment for the current session, so you should resolve this issue by finding the correct keyboard or the shortcut causing your problems. Note it will not reset a shortcut attached to the key:
```

xmodmap -e "keycode 50 = Shift_L"

```

---

