---
title: "Blank screen issues"
date: 2009-10-13
forum: Hardware
---

### Post by tinny on 2009-10-13
Hello

I have a really frustrating issue with Ubuntu 9.04

Ubuntu appears to be booting correctly (showing the progress bar), but 90% of the time instead of showing the login screen I am presented with a blank white screen. If I press ctrl + alt + F1 I am presented with a terminal session that looks fine.

The laptop im having issues with is a NEC Versa M400 - 240DW

Some details about the video card
```

> lspci

```
```

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

```

Im guessing there is something wrong with my xorg config???

Heres my xorg.conf

```

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    #Option        "UseFBDev"        "true"
EndSection

Section "ServerFlags"
    Option    "DontZap"    "False"
EndSection

```

Any ideas??? Thanks

---

