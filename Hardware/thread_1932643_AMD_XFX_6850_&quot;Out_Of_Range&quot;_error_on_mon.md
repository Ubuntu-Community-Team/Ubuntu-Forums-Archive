---
title: "AMD XFX 6850 &quot;Out Of Range&quot; error on monitor"
date: 2012-02-27
forum: Hardware
---

### Post by rld on 2012-02-27
Hi, I've tried installing fglrx drivers through jockey (not the post-release updates), the terminal and amd.com and it's always the same result: after a reboot, when X loads my monitor just shows an "Out of Range" error and I can't see anything, even though everything else is running in the background. I can still CTRL+ALT+F1 to open a console.

This is my /etc/X11/xorg.conf, haven't touched absolutely anything.

```
Section "Screen"
    Identifier "Default Screen"
    DefaultDepth 24
EndSection

Section "Module"
    Load "glx"
EndSection
```If it helps, my monitor is a ViewSonic VE710s and runs at 1280x1024@75Hz.

Thanks!

---

### Post by rld on 2012-03-02
Bump. I've kept looking and apparently this has something to do with lightdm

---

