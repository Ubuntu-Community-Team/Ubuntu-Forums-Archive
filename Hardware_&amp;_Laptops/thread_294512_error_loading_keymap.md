---
title: "error loading keymap"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by RanDinCarolina on 2006-11-06
I have Edgy on an AMD 3000+ XP and it has been working well. However, the last couple of days the keyboard has been locking up. The mouse works though. The Xorg.0.log gives 

```
error loading keymap /var/lib/xkb/server-0.xkm
```

I don't have the keyboard in the terminal either. If I do a hard reset, then the keyboard comes back until the next time. The only things that have changed are I took the last updates for the kernel and I installed BOINC and SETI.

I wonder if I need to reconfigure X just in case a setting got clobbered.



11/18/06 -Solved, sorta.   It only dies if I use the generic kernel, so I'll stick to the 386 for that machine.....

---

### Post by RanDinCarolina on 2006-11-21
I lied. The problem has not been solved. The keyboard still locks up. And X will not let me reconfig the keyboard.

---

