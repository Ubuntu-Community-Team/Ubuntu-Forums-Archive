---
title: "Driver ralink can not load firmware module"
date: 2014-10-22
forum: Hardware
---

### Post by andrey21 on 2014-10-22
# apt-get install firmware-ralink# ls /lib/firmware | grep rt...rt3070.bin...# modprobe rt3070FATAL: Module rt3070 not found.

---

### Post by andrey21 on 2014-10-22
What to do?

---

### Post by Yellow Pasque on 2014-10-22
> modprobe rt3070
The firmware file is named rt3070.bin, but the kernel module you actually use is a rt2800 module (I guess a lot of the various Ralink chipsets are similar enough to group them together). You probably want:
```
sudo modprobe rt2800usb
```

> apt-get install firmware-ralink
That is the package name Debian uses. Ubuntu uses firmware-linux (I think it's installed by default).

---

