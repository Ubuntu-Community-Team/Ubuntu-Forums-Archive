---
title: "Documate 262i installation problems"
date: 2011-09-11
forum: Hardware
---

### Post by kodb on 2011-09-11
I have a Xerox Documate 262i that I am using without problems via Virtualbox XP guest on one of the Lucid desktops at my office.
I have installed sane, libsane-extras, sane-utils and all those goodies.
I have tried both simple-scan and xsane.
Per the Sane manpages the 262i is supported by the avision backend.
The avision.conf file is present

Using sane-find-scanner yields the following output:
```
found USB scanner (vendor=0x04a7, product=0x04a7) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

```

but using scanimage -L yields nothing.

lsusb yields:
```
$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04a7:04a7 Visioneer 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I am stumped here.  Any suggestions?  Do I need to modify /etc/sand.d/avision.conf ?
If so what entries are needed since it seems the hardware is seen but not recognized by sane despite being listed as supported by the avision backend and the hardware works under the XP guest so it must be either a driver or conf problem under Lucid.
Thanks in advance
Bob

---

### Post by kodb on 2011-09-17
Any ideas anyone?
Still stuck here.
Bob

---

