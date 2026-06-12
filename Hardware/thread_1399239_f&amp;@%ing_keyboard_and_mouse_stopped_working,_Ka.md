---
title: "f&amp;@%ing keyboard and mouse stopped working, Karmic, Dell Inspiron 6400"
date: 2010-02-05
forum: Hardware
---

### Post by rshetye on 2010-02-05
Had to do the following to get it up and running again.

```
apt-get install xserver-xorg-input-kbd
```

/etc/X11/xorg.conf
> Section "ServerLayout"
        Identifier      "Default Layout"
        Option "AutoAddDevices" "off"
        Option "AllowEmptyInput" "off"
EndSection


Either some developer has his head stuck in the sand or some package maintainer is dozing off.... this is the third RELEASE I've encountered such problems... 8.10, 9.04 and now 9.10... Ubuntu needs to get its act into shape....

---

