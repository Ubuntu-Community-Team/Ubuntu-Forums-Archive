---
title: "Ubuntu 12.10 and Cyborg R.A.T. 3 Mouse"
date: 2012-12-18
forum: Hardware
---

### Post by jet4fire on 2012-12-18
For the excellent work the mouse, you must do some moves

in file ```
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
```

add this code

```

Section "InputClass"
    Identifier "Mouse Remap"
    MatchProduct "Saitek Cyborg R.A.T.3 Mouse"
    MatchDevicePath "/dev/input/event*"
    Option "ButtonMapping" "1 2 3 4 5 0 0 8 9 0 0 0 13 14"
EndSection

```

This all, enjoy!

---

### Post by elpiloto on 2013-04-09
I have a rat3 mouse, it worked ok, but the forward and back buttons at the side seems to dont work, any suggestion?

cheers

---

