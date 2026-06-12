---
title: "Logitech Quickcam Fusion in 9.04"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by Snuzzer on 2009-06-15
Hey.

I have a Logitech Quickcam Fusion which I just can't get working. I had it work in Ubuntu 8.10, but I can't get it work in 9.04.

I must admit, that I can't remember exactly how I dit it 8.10. I'm still a little new to Linux.

Can anyone help me, please?

When I have it connected to the PC and type in *lsusb*, it is correctly found:
```
Bus 001 Device 002: ID 046d:08c1 Logitech, Inc. QuickCam Fusion
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Thanks in advance.
Simon B. Støvring, Denmark

---

### Post by Snuzzer on 2009-06-16
Bump. Anyone knows?

---

### Post by rhewt on 2010-01-09
sudo rmmod uvcvideo
sudo modprobe uvcvideo

It should work now (you may have to do that everytime it doesn't work). Has to do with the order the modules are loaded

---

