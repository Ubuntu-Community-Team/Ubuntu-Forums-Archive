---
title: "need help mapping keys (add accents w/ super modifier)"
date: 2008-11-27
forum: General Help
---

### Post by sharkbaitIMH on 2008-11-27
I'm new to the forums. Sorry if i'm posting in wrong place.

I want to make my super button add an accent certain characters i press with it. For example, <Super+e> giving é, <Super+E> giving É, <Super+n> giving ñ, <Super+?> giving ¿, etc... I have no idea how to do this because it seems most people just use a compose/multi-key for accented characters.

I attached a txt I was using as notes on the relevant characters I got from xev:

Holding the super button changes the state from 0x0 to 0x40 (0x1 to 0x41 if shift is held) but that doesn't change the associated keysym. Seems like changing what keysym the keycode pulls up from an X(mb)LookupString in a specific state (i.e. 0x40 and 0x41) might do it.

Then again I have no idea what I'm doing with this stuff. I don't even know what the keycodes/keysyms or X(mb)LookupString really are. I've been messing around where I can and have reached a dead end.

Thanks

btw, i'm on xubuntu so i think the super key CAN be used as a modifier

---

### Post by ashmew2 on 2008-11-28
Try running xmodmap in a terminal , On my system it gave the following output , So im pretty sure Super IS a modifier..

> xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
**mod4        Super_L (0xce)**,  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)


You have awakened the Keyboard Mapping demon in me once again...Thanks! muahahhahahahah..

---

### Post by ashmew2 on 2008-11-28
[http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560)

That might help you..

---

### Post by earthtux on 2009-02-02
may I ask whats the command to show desktop? so i can put it in metacity's command box?
thx!!

---

