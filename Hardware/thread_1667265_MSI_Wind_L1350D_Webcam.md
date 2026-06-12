---
title: "MSI Wind L1350D Webcam"
date: 2011-01-14
forum: Hardware
---

### Post by bman1985 on 2011-01-14
Hi, I just installed Ubuntu 10.10 (not netbook remix) on my wind L1350D netbook. When I go into cheese it doesn't recognize my webcam. I tried turning it on using the appropriate FN button, but it didn't work still. 
 
Anybody able to get theirs to work?

---

### Post by kosokuadam on 2011-01-15
I've had an MSI machine before as well, and I've had a myriad of problems getting Ubuntu to regognise hardware, but with mine it was mainly the wireless functions. Does it even recognise that the webcam exists, or is it just like it's not there?

---

### Post by bman1985 on 2011-01-16
I'm not really sure, where would it show up? I just tried using it in cheese and emphathy messenger and it said no webcam detected.

---

### Post by IcarusR on 2011-01-16
Try running the following in a terminal & see if any thing that shows up could be webcam.

```
lsusb
```

---

### Post by Sn3rk on 2012-04-16
> **IcarusR said:**
> Try running the following in a terminal & see if any thing that shows up could be webcam.

```
lsusb
```

 Just did an lsusb and got the following output: ```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```What should I be looking for, to activate my webcam?

---

