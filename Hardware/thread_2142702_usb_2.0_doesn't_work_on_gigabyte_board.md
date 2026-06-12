---
title: "usb 2.0 doesn't work on gigabyte board"
date: 2013-05-06
forum: Hardware
---

### Post by nooblinuxuser0231 on 2013-05-06
I built a desktop pc and tried to install ubuntu 12.10 on a gigabyte 990-fxa ud3 board, but only my usb 3.0 ports worked. I googled a bit and made sure legacy support was on in the bios, but I can't come up with any other possible solutions. I also tried the most recent version of debian, and it had the same problems. This was on a live cd. Does anyone have an idea on how to correct this problem? I'd like to know if it can be solved before installing ubuntu. Thanks!

---

### Post by grahammechanical on 2013-05-06
There are two commands that you can run from a live session to see if Ubuntu detects your USB ports.

```
lspci
```
and
```
lsusb
```

If you want to be baffled by information run

```
lspci -v
```
and
```
lsusb -v
```

Regards.

---

