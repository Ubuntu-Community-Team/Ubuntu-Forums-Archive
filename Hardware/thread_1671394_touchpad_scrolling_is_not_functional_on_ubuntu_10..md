---
title: "touchpad scrolling is not functional on ubuntu 10.10"
date: 2011-01-20
forum: Hardware
---

### Post by kidalive on 2011-01-20
Greetings.
Ubuntu seems have not identified my touchpad, the scrolling function is not working.
I checked the System-Preferences-Mouse option, no trackpad Tab founded.
I did cat '/proc/bus/input/devices' command and noted. Please help me fix this bug of
this amazing OS.
thanks in advance.

---
Architecture: i386
DistroRelease: Ubuntu 10.10
EcryptfsInUse: Yes
InstallationMedia: Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
root@:~# dmesg | grep mouse
[11150.175600] psmouse serio4: ID: 10 00 64
root@:~# lsmod | grep psmouse
psmouse                59033  0 
root@:~# uname -a
Linux  2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

---

### Post by kidalive on 2011-01-20
more details:
```
lshal|grep input.product
  input.product = 'Lid Switch'  (string)
  input.product = 'Sleep Button'  (string)
  input.product = 'Power Button'  (string)
  input.product = 'Video Bus'  (string)
  input.product = 'Power Button'  (string)
  input.product = 'PS/2 Generic Mouse'  (string)
  input.product = 'AT Translated Set 2 keyboard'  (string)
  input.product = 'SI'  (string)
  input.product = 'SI'  (string)
```

---

