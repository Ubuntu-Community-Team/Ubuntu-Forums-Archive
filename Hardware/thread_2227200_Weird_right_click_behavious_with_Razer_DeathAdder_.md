---
title: "Weird right click behavious with Razer DeathAdder 2013"
date: 2014-05-31
forum: Hardware
---

### Post by nwarrenfl on 2014-05-31
Hi,

My Razer DeathAdder 2013 behaves strangely when right clicking.
Sometimes the context menu closes directly, sometimes it clicks twice (which chooses a menu item and closes it), sometimes it works.

When this happens, holding the button keeps the menu open, but is very annoying.

I have no idea why, on Windows it works without any problems. Is there anyway i can debug this?

I tried this to debug, as you can see it presses and releases twice sometimes:
```
double@SATURN ~ $ xev | grep Button
ButtonPress event, serial 37, synthetic NO, window 0x4400001,
ButtonRelease event, serial 37, synthetic NO, window 0x4400001,
ButtonPress event, serial 37, synthetic NO, window 0x4400001,
ButtonRelease event, serial 37, synthetic NO, window 0x4400001,
double@SATURN ~ $
```

Thanks in advance :)

---

