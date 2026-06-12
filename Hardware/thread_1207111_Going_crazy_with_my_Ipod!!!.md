---
title: "Going crazy with my Ipod!!!"
date: 2009-07-07
forum: Hardware
---

### Post by evil_reindeer on 2009-07-07
Hi, I've been using Ubuntu 9.04 for abouth a month now without any problem, it used to recognize my Ipod normally, but lately when i connect the Ipod, it doesn't recognize it anymore, i mean, the ipod connects normally, but Ubuntu does nothing, I've tried with Gtkpod, Hipo ,Yamipod,Rhytmbox,Amarok and Songbird, but nothing happens. Please help me, I want to put some music but I cant!!!

By the way, english is not my native language so I don't know if my grammar is Ok, and for some strange reason i can't access the Ubuntu forums on my language , but nevermind, please help me!!!

---

### Post by IamWayne on 2009-07-07
Do a google search on iPod Nano Linux.

---

### Post by tgalati4 on 2009-07-08
Plug in your iPod and in a terminal:

```
dmesg | tail -50
```

---

### Post by evil_reindeer on 2009-07-08
forget it, I reinstall the whole system :D
now everything is normal
anyway, thank you very much

---

### Post by tgalati4 on 2009-07-08
You normally don't need to reinstall.  Sometimes the iPod file system needs cleanup before it will mount.

The dmesg command will show the errors.

---

