---
title: "USB DVD Drive Won't Mount"
date: 2010-10-23
forum: Hardware
---

### Post by fraser_m on 2010-10-23
Since I upgraded to 10.10, I've been having trouble getting my external DVD drive to mount. The "CD/DVD Drive" icon appears for a few seconds in Computer, but then disappears without mounting the disk. It used to work fine with 10.04.

lsusb (device in question in bold):```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 031: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter**
Bus 001 Device 028: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 027: ID 05ac:0221 Apple, Inc. Aluminum Keyboard (ISO)
Bus 001 Device 026: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 018: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```dmesg:```
[74742.045283] usb 1-3: new high speed USB device using ehci_hcd and address 31
[74742.185381] usb-storage 1-3:1.0: Quirks match for vid 05e3 pid 0701: 520
[74742.185492] scsi14 : usb-storage 1-3:1.0

```Any suggestions?

---

### Post by doubtful wisdom on 2010-11-06
Have the same problem with 10.10, however this is a new install so there is no history.  DVD drive is there until media loads, then gone, poof.

This is a dual boot older laptop.  XP sees the USB attached DVD writer and works correctly.  The post that I am replying to is the only other mention of the problem I know of.

---

### Post by Gonzo_Dark on 2010-11-09
I have the exact same problem (Ubuntu 10.10)

K3B can read/rip CD's and DVD's
VLC can play the CD's and DVD's
and I can mount the CD/DVD with this command: sudo mount /dev/sr0

But I can't burn and the system does not recognize my optic drive after I have inserted the disk.

---

### Post by coffeecat on 2010-11-27
> **fraser_m said:**
> ```
**Bus 001 Device 031: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter**
```

For device ID 05e3:0701 have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1618085](http://ubuntuforums.org/showthread.php?t=1618085)

Some workarounds for Maverick and a link to a bug report.

---

