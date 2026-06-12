---
title: "Unable to mount USB stick"
date: 2009-11-28
forum: Hardware
---

### Post by paul8472 on 2009-11-28
My system (9.10) has suddenly started not mounting USB devices.  I think it happened after following this guide:

[http://ubuntuforums.org/showthread.php?t=869229&highlight=6239582](http://ubuntuforums.org/showthread.php?t=869229&highlight=6239582)

When plugging in the stick it is detected by the system (the first entry)

lsusb:
```
Bus 002 Device 012: ID 07ab:fcf6 Freecom Technologies 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 046d:abd0 Logitech, Inc. 
Bus 006 Device 003: ID 046d:c50c Logitech, Inc. Cordless Desktop S510
Bus 006 Device 002: ID 0451:2036 Texas Instruments, Inc. TUSB2036 Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```but it doesn't look like it is assigned to a device (e.g. sdb or whatever)

dsmeg

```
[ 9278.416035] usb 2-6: new high speed USB device using ehci_hcd and address 12
[ 9278.551761] usb 2-6: configuration #1 chosen from 1 choice
```No further entries from dsmeg.

I've had quite a look around with no luck to date. Any ideas?

Thanks in advance

Paul

---

### Post by paul8472 on 2009-11-29
Ignore the message above, it's fixed itself

---

