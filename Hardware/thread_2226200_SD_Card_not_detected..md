---
title: "SD Card not detected."
date: 2014-05-26
forum: Hardware
---

### Post by davesbrain on 2014-05-26
I've tried two SD cards and neither are detected.  Card reader is detected.  USB in same device works fine.
Ubuntu 14.04

[ATTACH=CONFIG]253454[/ATTACH]

```
davidjr@desktop:~$ sudo lsusb
[sudo] password for davidjr: 
Bus 002 Device 002: ID 0cf2:6230 ENE Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 0461:4d0f Primax Electronics, Ltd HP Optical Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:09a4 Logitech, Inc. QuickCam E 3500
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0461:4d81 Primax Electronics, Ltd Dell N889 Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by matt_symes on 2014-05-28
Hi

What's the output from the tail end of dmesg after pluging in a sd card into the reader ?

Kind regards

---

### Post by davesbrain on 2014-05-29
I got it working.  I just unplugged it, booted up the machine. Shutdown, plugged it back in then booted again.

---

