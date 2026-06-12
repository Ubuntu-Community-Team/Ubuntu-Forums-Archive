---
title: "USB WIFI Adapter not accepted"
date: 2011-06-10
forum: Hardware
---

### Post by complience on 2011-06-10
I have a USB wifi adapter I was having a driver problem with so I updated a patched version of compat, now the adapter is not detected by the system what so ever.

LSUSB does not show it

but the syslogs to detect when connected I get this:


Jun 10 13:53:52 ubuntu-laptop kernel: [  876.921803] usb 2-1.2: new full speed USB device using ehci_hcd and address 18
Jun 10 13:53:52 ubuntu-laptop kernel: [  877.329433] usb 2-1.2: device not accepting address 18, error -32
Jun 10 13:53:52 ubuntu-laptop kernel: [  877.329583] hub 2-1:1.0: unable to enumerate USB device on port 2


I do not appear to have a ehci_hcd module

ubuntu-laptop:~$ sudo modprobe ehci_hcd
ubuntu-laptop:~$ sudo rmmod ehci_hcd
ERROR: Module ehci_hcd does not exist in /proc/modules


Ive no idea how the module was deleted but usb surely needs it?
Ubuntu 32bit
11.04
Adapter:ALFA AWUS036NEH

---

### Post by complience on 2011-06-10
I have tested the adapter on a different machine with Ubuntu 10.10 and on the same machine with backtrack 4

The same error appears to happen - so im thinking this is a hardware issue

---

