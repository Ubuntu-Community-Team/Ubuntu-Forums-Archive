---
title: "devkit-power does not detect battery on ACER"
date: 2009-12-18
forum: Hardware
---

### Post by fenrasa on 2009-12-18
Hi,

I've got this little issue with my GNOME-power-manager. I use Ubuntu 9.10 on my Acer TravelMate 8471.
GPM does not detect the battery. It thinks the laptop runs on cable.

devkit-power -d says:
Device: /org/freedesktop/DeviceKit/Power/devices/battery_BAT0
native-path: (null)
power supply: no
[...]
updated: Thu Jan 1 01:00:00 1970

but cat /proc/acpi/battery/BAT0/state
shows:
present: yes
capacity state: ok
[...]
remaining capacity: 4570 mAh.
[...]

that means Something finds the battery.
I need help. :)

~Fenrasa

---

### Post by fenrasa on 2009-12-18
**solved**

Installing *Devicekit-power 013 packages for Karmic (160.4 KiB,         application/x-tar)*
from the following website solved my issue:
[https://bugs.launchpad.net/fedora/+source/devicekit-power/+bug/434771](https://bugs.launchpad.net/fedora/+source/devicekit-power/+bug/434771)

:guitar:

---

