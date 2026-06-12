---
title: "Canon CanoScan LiDE 210 looks dead in 14.04.03"
date: 2015-08-16
forum: Hardware
---

### Post by djdg on 2015-08-16
Hello everybody,

I have a Canon CanoScan LiDE 210 which gives no reaction at all under Ubuntu 14.04.03 on my pc.

lsusb gives:

```
Bus 006 Device 002: ID 8087:8000 Intel Corp. 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 046d:c069 Logitech, Inc. M500 Laser Mouse
Bus 003 Device 003: ID 046d:c328 Logitech, Inc. 
Bus 003 Device 002: ID 2109:3431  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 8087:8008 Intel Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04a9:190a Canon, Inc. CanoScan LiDE 210
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

When I try it on a Windows 7 32-bit laptop it gives a small reaction: you can hear the lightbar move a little, but that's all. When I install the drivers and other software it gives an internal error (Code:5,202,52).

Thanks in advance for trying to help me out.

Greetings,
Dirk-jan
The Netherlands

---

### Post by VMC on 2015-08-16
Here's my Canon output, and it works using Simple Scan

dmesg:```
[ 1484.473612] usb 2-2: new full-speed USB device number 3 using ohci-pci
[ 1484.696271] usb 2-2: New USB device found, idVendor=04a9, idProduct=2207
[ 1484.696283] usb 2-2: New USB device strings: Mfr=64, Product=77, SerialNumber=0
[ 1484.696291] usb 2-2: Product: CanoScan
[ 1484.696296] usb 2-2: Manufacturer: Canon
```
lsusb:
```
Bus 002 Device 003: ID 04a9:2207 Canon, Inc. CanoScan 1220U
```

edit: I see you  have 210. My 1220u is unsupported in Windows after 7, and Canon won't support it?!
VueScan works though.

---

### Post by djdg on 2015-08-17
In VueScan it is also recognised. There is a small movement of the lightbar, but furthermore no activity.

---

### Post by djdg on 2015-08-17
Offtopic: How do I change my signature as seen in my last post?

---

### Post by VMC on 2015-08-17
Maybe the belt slipped off or if it has gears, then maybe they are somehow disengaged. If it won't work then repair is the only option.
My Canon has a screw drive that I can plainly see. If its electronics are most likely not going to fix it. Opening the glass to inspect the drive gear may be your only option.

---

