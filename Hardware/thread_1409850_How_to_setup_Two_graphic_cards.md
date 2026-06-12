---
title: "How to setup Two graphic cards"
date: 2010-02-18
forum: Hardware
---

### Post by mattPiratt on 2010-02-18
Hello

 Im trying to set up 2 monitors conneted to 2 graphics cards:

1st) 
```

Section "Device"
Identifier "Card1"
Driver "intel"
VendorName "Intel Corporation"
BoardName "82G33/G31 Express Integrated Graphics Controller"
EndSection

```
...is onboard set in BIOS to always ON, and as secondary

2nd)
```

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 6200 TurboCache(TM)"
EndSection

```

is PCIE card, set in BIOS as primary (first init).

In Ubuntu 9.10 i got nVidia running. But no clue what to do to have Intel G31 working.

When I run manualy "X -configure", it generates me xorg.conf with information about both cards, but when I try to use this config file
```

X -config /home/[....]/xorg.conf

```
i go black.

Does anybody have clue?

---

### Post by scouser73 on 2010-02-18
I don't know about dual graphics cards but here's what I do to set up two monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - **X Server Display Configuration** will now start, now you can set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

---

