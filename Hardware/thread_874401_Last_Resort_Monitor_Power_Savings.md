---
title: "Last Resort Monitor Power Savings"
date: 2008-07-29
forum: Hardware
---

### Post by 42reasons on 2008-07-29
Hello, to whoever can help me, please do...

this is my last resort efore buying a new moniter which i really dont want to do.  So heres the problem, I turn on my Dell Inspiron 600m laptop, see the unbuntu load, then proceed to enter my name and password in the login screen...

then i get a pale yellow screen... and my monitor shuts down and goes into power saving mode, i even get to hear the music of me logging in but cannot see anything, please help!

btw, my old laptop does not have its old attached lid, i have it connected to a dell box moniter.

---

### Post by Rocket2DMn on 2008-08-03
I suggest booting into the recovery mode kernel terminal and running
```
dpkg-reconfigure xserver-xorg -phigh
reboot
```
Ideally you should never have attempted to install restricted ATI drivers since this laptop's video card is too old for them.  Let me know if you have.  Buying a new monitor will probably not help with this problem since it seems that X isn't autodetecting your setup properly.  You may want to fiddle with the Fn+F8 key since dual monitors doesn't work very well on these old ATI cards, I don't think the open source ati drivers support dual head, though cloning may be OK.

---

