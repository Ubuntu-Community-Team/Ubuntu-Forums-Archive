---
title: "XM Radio Pioneer XMP3 player does not mount."
date: 2009-03-27
forum: Hardware
---

### Post by TerpInHotLanta on 2009-03-27
So I have a bit of an annoying problem: when I plug in my Pionner GEX-XMP3 player, I get the following message is /var/log/messages and /var/log/syslog:

```
Mar 27 10:01:47 Terpacket kernel: [  862.352127] usb 2-5: new high speed USB device using ehci_hcd and address 2
Mar 27 10:01:48 Terpacket kernel: [  862.498845] usb 2-5: configuration #1 chosen from 1 choice
```

Disconnecting and reconnecting the device:
```
Mar 27 10:11:09 Terpacket kernel: [ 1424.211353] usb 2-5: USB disconnect, address 2
Mar 27 10:11:29 Terpacket kernel: [ 1444.381037] usb 2-5: new high speed USB device using ehci_hcd and address 3
Mar 27 10:11:30 Terpacket kernel: [ 1444.526670] usb 2-5: configuration #1 chosen from 1 choice
```

lsusb:

```
Bus 002 Device 003: ID 08e4:0148 Pioneer Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b018 Chicony Electronics Co., Ltd Video Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

mtp-detect:
```
libmtp version: 0.3.0

Listing raw device(s)
   No raw devices found.
```

Going to /media/usb2 or usb3 did not show anything in the directory structure.

Previously, I have tried unloading ehci_hcd, but that did not do anything.

This device did mount as a "generic MTP device" in Windows XP SP3; although, I believe I read somewhere that this device is actually a USB mass storage-- not positive.

Also, libmtp does not list any support for this device.

Any ideas? Thanks in advance!

I'm running 9.04 (although this problem has persisted since I bought the player and was running 8.10).

---

