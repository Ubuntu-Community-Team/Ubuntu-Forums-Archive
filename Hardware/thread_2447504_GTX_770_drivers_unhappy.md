---
title: "GTX 770 drivers unhappy"
date: 2020-07-20
forum: Hardware
---

### Post by samwiebs on 2020-07-20
I've got a box from 2014 with a GTX 770 video card and ubuntu installed.  When the nvidia drivers are installed and active it boots to a purple screen and no further.  Ubuntu is running, and I can work cmd line by going Ctrl-Alt-F2.  Occasionally there are some fun artifacts of the GUI popping up when I"m in the cmd line mode.   If I activate the intel drivers (prime-select intel) the GUI works fine but with lower res and no multi screen.  At this point I've tried all the available nvidia drivers back to 390 and the open source ones as well.  Also tried rm the various modprove blacklist files and update-initramfs, and doing a complete apt-get purge and reinstall of drivers.  Card works fine when booted into Windows, so unlikely a hardware issue.

Are there older versions of nvidia driver's I should be using that aren't listed?  Any recommendations?

---

### Post by Autodave on 2020-07-20
What version of Ubuntu is that running?  Also please give us make and model od equipment.

---

### Post by mastablasta on 2020-07-21
you can use inxi to gather data.

```
inxi -Fz
```

or list hardware command then copy and paste here using code tags:

```
lshw -sanitize
```

GTX770 should be well suported.

---

