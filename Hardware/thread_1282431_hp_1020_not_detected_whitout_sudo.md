---
title: "hp 1020 not detected whitout sudo"
date: 2009-10-04
forum: Hardware
---

### Post by Ruslan T. on 2009-10-04
Hello.
I'm using Ubuntu 9.10 beta, kernel 2.6.31-11-generic.
My usb-printer is hp laserjet 1020. But it is not detected by lsusb:
```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
dmesg log after plug-in printer:
```
[23558.836847] usb 1-4: new high speed USB device using ehci_hcd and address 5
[23558.989752] usb 1-4: configuration #1 chosen from 1 choice
[23558.993521] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x03F0 pid 0x2B17
[23560.549277] usb 1-4: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

```
However lsusb with superuser's privileges:
```
$ sudo lsusb
Bus 001 Device 005: ID 03f0:2b17 Hewlett-Packard LaserJet 1020
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
How can I fix it?
p.s. other usb devices work good (such as scaner, flash).

---

### Post by Ruslan T. on 2009-10-04
:) Problem is solved:
```
sudo chown user /dev/bus/usb/001/005
```

---

