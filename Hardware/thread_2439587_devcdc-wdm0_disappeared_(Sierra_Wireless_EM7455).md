---
title: "/dev/cdc-wdm0 disappeared (Sierra Wireless EM7455)"
date: 2020-03-30
forum: Hardware
---

### Post by ronaldw2 on 2020-03-30
I was using my WWAN modem for years without any problem. Two weeks ago, WWAN suddenly stopped working. dmesg still shows "Sierra Wireless EM7455"

```
[   55.860708] usb 1-6: new high-speed USB device number 10 using xhci_hcd
[   55.881497] usb 1-6: New USB device found, idVendor=1199, idProduct=9078, bcdDevice= 0.00
[   55.881499] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   55.881500] usb 1-6: Product: Sierra Wireless EM7455 Qualcomm
[   55.881501] usb 1-6: Manufacturer: Sierra Wireless, Incorporated
[   55.881502] usb 1-6: SerialNumber: LF73440293021020
[   55.882575] qcserial 1-6:1.0: Qualcomm USB modem converter detected
[   55.882646] usb 1-6: Qualcomm USB modem converter now attached to ttyUSB0
```

lsusb shows
```
Bus 001 Device 010: ID 1199:9078 Sierra Wireless, Inc. Sierra Wireless EM7455 Qualcomm
```

The problem seems to be that the device cdc-wdm0 is not created anymore. Any ideas why?

---

