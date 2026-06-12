---
title: "Dell D800 keyboard problem"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by bigfan on 2007-11-02
Hi,

  Sometimes (ie. after few days of work) Shift, Ctrl and Caps Lock suddenly stop working. If I run xev, every use of them is properly reported. Restart of window manager doesn't help. When I change console (using chvt), all these keys work without a problem. When I return back to X session, they stop. If I run another X session, everything is all right. The only method to get these keys back working is to restart XServer. There are no errors in Xorg.0.log, .xsession-errors log or messages. The same situation occured on Debian stable/unstable and on different window managers...
Can anyone help?

My keyboard configuration:
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "pl"
EndSection

```

---

