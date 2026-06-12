---
title: "xmodmap: remap num lock?"
date: 2009-02-01
forum: Hardware
---

### Post by Mrs.Columbo on 2009-02-01
Hi,

Since i quite frequently need to enter numbers in a 1e5 format I want to remap the numlock key to e (so that i can type one-handedly). 
However, i somehow need to activate the number block, so i decided to map Num_Lock on the Scroll_Lock key.
with 

```
xmodmap -e "keysym Scroll_Lock = Num_Lock"
```

xev gives Num_Lock as correct event, however i miss the following (quoted from xev before changing the original Num_Lock key)

```
PropertyNotify event, serial 35, synthetic NO, window 0x2400001,
    atom 0x178 (XKLAVIER_STATE), time 10891125, state PropertyNewValue

```
For comparison, i posted the original numlock xev output and the one of the remapped scroll lock:
[http://pastebin.com/f3558ea1c]("http://pastebin.com/f3558ea1c")

Any ideas how i can fix this? Would be brilliant if i could get this to work -though actually I consider it a hardware issue that producers should fix by just adding an e key to the numlock. Screw those multimedia keys, get practical...;)

MC

---

### Post by roberto.tomas on 2012-01-16
(Ubuntu 11.10)
I have a startup application entry I wrote, that just calls xmodmap ~/.Xmodmap
in it, I put the following:
>  remove Lock = Num_Lock
 keysym Num_Lock = Scroll_Lock
 keysym Scroll_Lock = Num_Lock
 add mod2 = Num_Lock
 keycode 77 = e
 remove mod2 = e

...then you need to set the numlock in the **on** state by default if you like in the  keyboard preferences. Or turn it on/off when you like by pressing Scroll Lock (this will also turn on the scroll lock)

**Edit**: ***NOT FIXED*** *(thought it was fixed with addition of remove mod2)* - Well it seems that this almost works. But the numlock key will, in addition to typing "e", also change the numlock state when numlock is in the on state, but will not change it when it is in the off state. Going to the commandline and running:
> xmodmap -e "remove mod2 = e"
*will* fix it. But adding that line to .Xmodmap and running that during start up *will not* fix it.

I think that could be considered a bug. Shouldn't anything that happens in a custom startup script happen after any other changes made by the windowing system?

---

