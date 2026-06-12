---
title: "usb-hard drive doesn't mount"
date: 2016-02-29
forum: Hardware
---

### Post by bestoe on 2016-02-29
Dear all,

here is the problem:
I have here an internal hard drive in an external case, which can be connected via sata or usb cable. The problem is now, that the drive is not mounting currently. Originally we had it running on the sata cable, but i changed this now to usb. It still doesn't mount. Basically I'm looking for the source of the problem: Is the disk broken or is it the transmission by the external case - or what?

Now, if I plug the whole setup in as usb, i get the following output:
```

dmesg

[120765.778502] usb 2-1.1: new high-speed USB device number 10 using ehci-pci
[120765.871194] usb 2-1.1: New USB device found, idVendor=13fd, idProduct=160f
[120765.871200] usb 2-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0

```

The hard disk itself is found and identified:
```
 lsusb
Bus 002 Device 003: ID 05c6:9204 Qualcomm, Inc. 
Bus 002 Device 010: ID 13fd:160f Initio Corporation RocketFish SATA Bridge [INIC-1611]
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The system is running a
```
uname -a
Linux bs 3.13.0-79-generic #123-Ubuntu SMP Fri Feb 19 14:27:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

Does anybody have a hint where the problem exactly is?
Thanx!

---

### Post by X-RED_Tech on 2016-02-29
Does it work directly over SATA?

---

### Post by bestoe on 2016-10-18
Well, o.k., obviously the hard drive wasn't fixed correctly in the case for the external usage. The case didn't seem to work properly anymore. Yes, the case and the computer had a socket for external SATA usage. Both didn't work. It seems the connection was somewhat established (so there was a notification, of the drive), but the connection somehow didn't work properly, so the drive couldn't be mounted. A new case for the hard drive solved the problem.

---

### Post by MartyBuntu on 2016-10-18
Good to hear.

---

### Post by ajgreeny on 2016-10-18
Please mark as.solved from.the thread tools.menu up.top.
It is very helpful to users searching the forum.

---

