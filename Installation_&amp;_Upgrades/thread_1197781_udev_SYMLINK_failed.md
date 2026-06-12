---
title: "udev SYMLINK failed"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by petzler on 2009-06-26
Hi,

for my PVR 250 TV card I add the following lines to the /etc/udev/rules/100-mythtv-card.rules

```

DRIVERS=="ivtv", ATTR{name}=="ivtv? encoder MPG*", ATTRS{vendor}=="0x4444", ATTRS{device}=="0x0803", NAME="%k", GROUP="video", SYMLINK+="pvr-250/%k /dev/v4l/%k"
....

```

But it isn't fully working:

```

$ ll /dev/pvr-250/
insgesamt 0
lrwxrwxrwx 1 root root  7 2009-06-26 21:17 vbi0 -> ../vbi0
lrwxrwxrwx 1 root root  9 2009-06-26 21:17 video0 -> ../video0
lrwxrwxrwx 1 root root 10 2009-06-26 21:17 video24 -> ../video24
lrwxrwxrwx 1 root root 10 2009-06-26 21:17 video32 -> ../video32

```

works, but:

```

$ ll /dev/v4l/
insgesamt 0
drwxr-xr-x 2 root root 120 2009-06-26 21:10 by-path

```
don't. What happens here? nextview expects the devices here ...

Thanks
Olaf

---

