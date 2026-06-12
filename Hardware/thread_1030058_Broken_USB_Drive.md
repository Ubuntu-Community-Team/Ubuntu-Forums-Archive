---
title: "Broken USB Drive"
date: 2009-01-04
forum: Hardware
---

### Post by farmerpoe on 2009-01-04
I've got a Sony Microvault 2GB USB Drive which stopped working after being unsafely removed from a Windows PC. It doesn't show up on Ubuntu, and i can't get it to mount so i can format the thing.

Without drive plugged in:
$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

With the drive plugged in, lsusb gives the same result, but takes several minutes.

Have tried GParted, which can't detect it either.

So, is there any way to format the drive so it can be used?
Thanks in advance!

---

