---
title: "Deleted my graphics drivers?"
date: 2008-11-15
forum: General Help
---

### Post by Sontra on 2008-11-15
Edit: Fixed it. The recover menu's autofix solved everything.

Heyo,

So I was attempting to update my nVidia graphic drivers because of a framerate problem I was experiencing in WoW. And, from my guess, I actually deleted them instead of updated. Here's what happens.

I start the machine and it goes through a normal boot until I reaches ""Running local boot scripts". The screen flickers a few times and then shuts down. But it continues loading Ubuntu. I know this because I hear the usual loading noises and it makes it all the way to the login screen. I'm even able to log in and, presumably, it makes it all the way to the desktop and then just sits there since I can't do anything with it.

I don't know how to fix the problem. I presume I'll need to be in recovery mode (which I can do), but I don't know what to do once there.

Anyone able to help?

---

### Post by taurus on 2008-11-15
Maybe you can try to revert back to the default driver, nv, for your nVidia graphic card.  From the recovery mode, run

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by Sontra on 2008-11-15
Thanks taurus. As far as I understand, that's what the recovery menu did.

I think. Sometimes, I wonder if I even understand what I'm doing with Ubuntu. :D

---

