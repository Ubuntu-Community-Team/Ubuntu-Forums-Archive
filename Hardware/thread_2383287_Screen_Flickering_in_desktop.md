---
title: "Screen Flickering in desktop"
date: 2018-01-23
forum: Hardware
---

### Post by dark07 on 2018-01-23
screen keeps flickering in my monitor. how do i fix this?
cat /etc/lsb-release 
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS"
```

uname -a 
```
Linux akagami 4.13.0-31-generic #34~16.04.1-Ubuntu SMP Fri Jan 19 17:11:01 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```
lspci -nnk | grep -iA2 vga 
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:5902] (rev 04)
    DeviceName:  Onboard IGD
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]


```
env | grep DESK

```
DESKTOP_SESSION=ubuntu
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
XDG_SESSION_DESKTOP=ubuntu
XDG_CURRENT_DESKTOP=Unity

```

---

### Post by howefield on 2018-01-23
Thread moved to the "*Hardware*" forum.

---

