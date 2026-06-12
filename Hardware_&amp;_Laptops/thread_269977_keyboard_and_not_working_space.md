---
title: "keyboard and not working space"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by entereczek on 2006-10-02
Hi,

I've got a problem with keyboard in my laptop...Sometimes space doesnt work because its old... There is a button "<" near it and I want to make such thing, that when i press < button i get space on my screen. I used xev to see what code has that button but i dont know where to put it.
```
KeyPress event, serial 31, synthetic NO, window 0x2200001,
    root 0x44, subw 0x0, time 174176689, (167,-13), root:(590,297),
    state 0x0, keycode 94 (keysym 0x3c, less), same_screen YES,
    XLookupString gives 1 bytes: (3c) "<"
    XmbLookupString gives 1 bytes: (3c) "<"
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x2200001,
    root 0x44, subw 0x0, time 174176796, (167,-13), root:(590,297),
    state 0x0, keycode 94 (keysym 0x3c, less), same_screen YES,
    XLookupString gives 1 bytes: (3c) "<"

```
I want to use it in console and Xserver :)

Thanks from help
Entereczek

---

