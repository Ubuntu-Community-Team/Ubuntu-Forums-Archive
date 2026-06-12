---
title: "[SOLVED] XKB Configuration Error"
date: 2008-05-24
forum: Hardware
---

### Post by styphon on 2008-05-24
I notice the GBP symbol (SHIFT+3) wasn't working on my keyboard, just producing a 3 instead, so I tried changing the keyboard to the HP one (I have an HP laptop) and now every time I login I get this:
```

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
```

**The result of xprop -root | grep XKB**
```
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "uk", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "uk", "", ""
```

**The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd**
```
 layouts = []
 model = hpzt11xx
 overrideSettings = true
 options = []
```

I've tried switching to several different keyboard options but always get the same result. Please help.

---

### Post by styphon on 2008-05-25
*bump* Please can someone help? This is driving me nuts.

---

### Post by prshah on 2008-05-26
> **styphon said:**
> *bump* Please can someone help? This is driving me nuts.

Have you tried reconfiguring your keyboard settings with ```
sudo dpkg-reconfigure xserver-xorg
```?

---

### Post by styphon on 2008-05-26
I've managed to get the error away by setting it back to default and adding the £ symbol in by running a xmodmap command in the sessions manager.

---

