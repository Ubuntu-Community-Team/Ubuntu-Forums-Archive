---
title: "USB Ports not working"
date: 2008-11-04
forum: Hardware
---

### Post by davebridges on 2008-11-04
Around the time of the upgrade to 8.10 (it may have been before and i didnt notice), my USB ports stopped working on my Dell Inspiron 1150 laptop.  Devices are still getting power, but neither my mouse or iPOD dock are being recognized.  I ran lsusb and got:

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by davebridges on 2008-11-04
anyone?

---

### Post by davebridges on 2008-11-10
output of dmesg | grep usb:
```
[    2.633235] usbcore: registered new interface driver usbfs
[    2.633269] usbcore: registered new interface driver hub
[    2.640929] usbcore: registered new device driver usb
[    2.676332] usb usb1: configuration #1 chosen from 1 choice
[    2.781510] usb usb2: configuration #1 chosen from 1 choice
[    2.885043] usb usb3: configuration #1 chosen from 1 choice
[    2.989118] usb usb4: configuration #1 chosen from 1 choice
```

---

