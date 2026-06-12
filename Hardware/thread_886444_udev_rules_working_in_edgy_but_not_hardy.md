---
title: "udev rules working in edgy but not hardy"
date: 2008-08-11
forum: Hardware
---

### Post by scottishnarn on 2008-08-11
I have 2 tv tuners that udev mixes up so I wrote some udev rules to make some symlinks to work with mythtv. It all works fine in Edgy (32 bit) but I am now trying to install Hardy (64 bit) and the same rules don't work.

File: /etc/udev/rules.d/83-duplicate_devs.rules
```
KERNEL=="video*", DRIVER=="bttv", SYMLINK+="videobttv"
KERNEL=="video*", SYSFS{name}=="ivtv0 encoder MPEG", SYMLINK+="videoivtv"
```

Any ideas?

---

### Post by scottishnarn on 2008-08-13
OK, I sort of fixed it. I used some new rules which worked in Hardy ```
SUBSYSTEMS=="pci", ATTRS{vendor}=="0x4444", SYMLINK+="videoivtv"
SUBSYSTEMS=="pci", ATTRS{vendor}=="0x109e", SYMLINK+="videodvb"

```
However, I still don't know why the old rules work in Edgy but not in Hardy.

Any ideas would be help me really understand udev.

Thanks
David Petticrew

---

