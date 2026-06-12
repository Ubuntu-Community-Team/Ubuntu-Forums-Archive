---
title: "cdrom problem with toshiba portege m100"
date: 2008-03-29
forum: Hardware &amp; Laptops
---

### Post by ptero on 2008-03-29
i have a strange problem with my cdrom drive... while it's empty, the led is always on and dmesg is filled with following errors:
```
[  280.332000] sr: Sense Key : Medium Error [current] 
[  280.332000] sr: Add. Sense: Unable to recover table-of-contents
[  282.332000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00

```
while there's a disc in there, there are no problems at all.

---

### Post by ptero on 2008-03-30
btw, one more problem... i watched a dvd with vlc (without mounting it before manually or with ivman), now it wouldn't unmount or eject.

```

$ umount /dev/scd0
umount: /dev/scd0 is not mounted (according to mtab)

$ lsof /dev/scd0
COMMAND    PID USER   FD   TYPE DEVICE SIZE NODE NAME
dbus-laun 8002   ku    6u   BLK   11,0      7829 /dev/scd0
dbus-laun 8002   ku    7r   BLK   11,0      7829 /dev/scd0
dbus-daem 8003   ku    6u   BLK   11,0      7829 /dev/scd0
dbus-daem 8003   ku    7r   BLK   11,0      7829 /dev/scd0

```

is there a way to resolve this problem besides killing dbus?

---

