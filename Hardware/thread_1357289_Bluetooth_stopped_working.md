---
title: "Bluetooth stopped working"
date: 2009-12-17
forum: Hardware
---

### Post by HeretikSaint on 2009-12-17
I had my bluetooth usb micro-dongle hooked up and it was working fine.  It has suddenly stopped working for no reason.  It no longer lights up as it once did.  I'm using Karmic Koala.

Here is the output of lsusb | grep Blue
```
Bus 002 Device 005: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
```

Here is the output for hciconfig:
```
hci0:	Type: USB
	BD Address: 00:02:72:1D:75:58 ACL MTU: 1017:8 SCO MTU: 64:8
	UP RUNNING PSCAN ISCAN 
	RX bytes:953 acl:0 sco:0 events:26 errors:0
	TX bytes:358 acl:0 sco:0 commands:26 errors:0

```

Any ideas?

---

