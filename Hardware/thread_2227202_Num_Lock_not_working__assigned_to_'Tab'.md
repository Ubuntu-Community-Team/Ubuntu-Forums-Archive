---
title: "Num Lock not working / assigned to 'Tab'"
date: 2014-05-31
forum: Hardware
---

### Post by 2uQ6KKAD on 2014-05-31
Hey guys.

I recently installed Kubuntu 14.04 and ever since then didn't  get my Num Pad to work. I can use the arrows, pgup, pgdown, but when  I try to activate the Numbers by hitting Num Lock, nothing happens.  Instead, it writes a Tabulator in any text editor. In terminal, it  activates the command completion, so it seems to be a real tab signal. 

I used xev and indeed, the Num Lock key (key 77) was assigned to 'Tab'. So I used
```
xmodmap -e "keycode 77 = Num_Lock"
```
to remap it. Now, xev shows me this:
```
KeyPress event, serial 40, synthetic NO, window 0x5e00001,
    root 0x254, subw 0x0, time 3886041, (-383,371), root:(470,394),
    state 0x0, keycode 77 (keysym 0xff7f, Num_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

So, the remapping seems to have worked, but the Num keys are still not working.
It might be an issue with the german NEO layout that I have set up as  default, but switching to a different layout didn't help. And yes, I  made sure that the option "control mouse cursor with arrow keys" is  disabled.

  I have no idea what the problem is. Any ideas?

---

### Post by VMC on 2014-05-31
I'm, unsure what your code is doing, but have you tried: SystemSettings > InputDevices > Keyboard > NumLock = TurnOn

---

### Post by 2uQ6KKAD on 2014-05-31
Nope, that didn't help except for the fact that now, my shortcut 'Alt+Tab' to switch windows isn't working anymore.  -_-
Neither does the Fn key.

About my code: xev prints a message to stdout whenever I hit a key. Line 3 of the second code snippet says that the key with the number 77, which happens to be my Numlock key, is mapped to the Function 'Num_Lock'. So, everything should be fine. But it's not working.

---

