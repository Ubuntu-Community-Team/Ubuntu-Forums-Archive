---
title: "Intel X4500HD in Sony SR190.... Screen Resolution"
date: 2008-12-02
forum: Hardware
---

### Post by Dracojk on 2008-12-02
How do you set the resolution in Ubuntu?  The only options I'm given in the System menu is up to 800x600.

---

### Post by theozzlives on 2008-12-02
try editing your /etc/X11/xorg.conf as root

---

### Post by Dracojk on 2008-12-02
I tried that... here's what I put:


```
Section "Device"
    Identifier  "device0"
    Driver      "vesa"
EndSection

Section "Monitor"
    Identifier      "monitor0"
    DisplaySize     285 179
    HorizSync       29-60
    VertRefresh     0-60
    Modeline        "1280x800" 68.56 1280 1336 1472 1664 800 801 804 824 -HSync +Vsync
EndSection


```

---

