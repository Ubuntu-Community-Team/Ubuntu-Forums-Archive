---
title: "USB hub problem"
date: 2010-11-03
forum: Hardware
---

### Post by raffaele181188 on 2010-11-03
I'm keeping getting error from the kernel: cannot enumerate device on port (1|2|3|4) since 1 week. I don't remember whether I updated the kernel or not, the problem is that since I connect using an USB wifi Internet which in turn is connect to the hub, when the error is triggered (which happens ~10 min after login) I cannot use the Internet connection anymore. Also USB drives stop working, and dmesg reveals error such as "forcedeth[...] for device MSI-MXI" and similar. How can I fix this?

---

### Post by IcarusR on 2010-11-03
Try using a powered hub.

---

### Post by TSJason on 2010-11-03
I had a similar problem from a bad usb cable (connecting the hub to the port).

---

### Post by raffaele181188 on 2010-11-03
But I use this hub since 1+ year!!! And everything works fine.. Also, if I connect the hub to another computer it works. The problem is there since 1 week and is very frustrating, since the wifi dongle driver (a ralink based chip) also has its very own set of bugs!! (and of course, wicd also has its set of bug). I need an internet connection, nobody has managed to overcome this problem yet?

---

### Post by raffaele181188 on 2010-11-03
SOLVED
I added the following line to /etc/modprobe.d/forcedeth.conf
```

options forcedeth msi=0 msix=0

```
Now everything seems ok

---

