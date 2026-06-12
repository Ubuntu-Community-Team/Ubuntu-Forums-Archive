---
title: "Acer 5739G Video Problem"
date: 2009-12-16
forum: Hardware
---

### Post by Th1cKA on 2009-12-16
When i install NVidia video drivers the video becomes like this:
[[IMG]http://img99.imageshack.us/img99/3358/pic0034j.th.jpg[/IMG]](http://img99.imageshack.us/i/pic0034j.jpg/)
What to do to get it fixed?

---

### Post by flanagan on 2009-12-18
You will need to edit /etc/X11/xorg.conf and make sure the "ModeValidation" "NoTotalSizeCheck" option is present. In that file, my screen section now reads:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ModeValidation" "NoTotalSizeCheck"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

