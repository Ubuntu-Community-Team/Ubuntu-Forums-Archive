---
title: "USB Thumbdrive Fails to Mount: Need help with Data Recovery."
date: 2014-09-03
forum: Hardware
---

### Post by trinsic1 on 2014-09-03
Hi I have a USB memory stick that detects and will not read on any system I have. I tried it on two other PC's but it wont mount.
DMESG: 
```
[   31.370251] usb 5-2.3: USB disconnect, device number 5
[   31.499248] usb 5-2.4: USB disconnect, device number 6
[   31.639249] usb 5-2.2: USB disconnect, device number 4
[   32.357244] usb 5-2.2: new full-speed USB device number 7 using uhci_hcd
[   32.468248] usb 5-2.2: New USB device found, idVendor=0451, idProduct=2046
[   32.468253] usb 5-2.2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   32.471310] hub 5-2.2:1.0: USB hub found
[   32.473375] hub 5-2.2:1.0: 4 ports detected
[   32.681251] usb 5-2.3: new full-speed USB device number 8 using uhci_hcd
[   32.794249] usb 5-2.3: New USB device found, idVendor=0451, idProduct=1446
[   32.794255] usb 5-2.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   32.797312] hub 5-2.3:1.0: USB hub found
[   32.799415] hub 5-2.3:1.0: 4 ports detected
[   33.009250] usb 5-2.4: new low-speed USB device number 9 using uhci_hcd
[   33.143248] usb 5-2.4: New USB device found, idVendor=046d, idProduct=c00c
[   33.143255] usb 5-2.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   33.143260] usb 5-2.4: Product: USB Mouse
[   33.143264] usb 5-2.4: Manufacturer: Logitech
[   33.162108] input: Logitech USB Mouse as /devices/pci0000:00/0000:00:10.0/usb5/5-2/5-2.4/5-2.4:1.0/input/input16
[   33.162301] hid-generic 0003:046D:C00C.0004: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:10.0-2.4/input0
[   40.887304] ISO 9660 Extensions: Microsoft Joliet Level 3
[   40.922858] ISOFS: changing to secondary root
[   67.636033] usb 6-1: new low-speed USB device number 2 using uhci_hcd
[   67.760028] usb 6-1: device descriptor read/64, error -71
[   67.984033] usb 6-1: device descriptor read/64, error -71
[   68.200031] usb 6-1: new low-speed USB device number 3 using uhci_hcd
[   68.324027] usb 6-1: device descriptor read/64, error -71
[   68.552029] usb 6-1: device descriptor read/64, error -71
[   68.768034] usb 6-1: new low-speed USB device number 4 using uhci_hcd
[   69.184031] usb 6-1: device not accepting address 4, error -71
[   69.296028] usb 6-1: new full-speed USB device number 5 using uhci_hcd
[   69.712032] usb 6-1: device not accepting address 5, error -71
[   69.712045] hub 6-0:1.0: unable to enumerate USB device on port 1
[  300.780650] Program lshw tried to access /dev/mem between ff000->101000.
[  308.606266] Program lshw tried to access /dev/mem between ff000->101000.
[  441.667031] Program lshw tried to access /dev/mem between ff000->101000.
```

It doesnt show up in lsusb
root@bench:/home/trinsic# lsusb
```
Bus 005 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 10d5:0001 Uni Class Technology Co., Ltd 
Bus 005 Device 007: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 005 Device 008: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 005 Device 009: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
```

Does anyone have any suggestions? I just want to recover the data from this device. Can that be done without getting the device to connect to the os?

---

### Post by trinsic1 on 2014-09-04
Nobody has any suggestions on this?

---

### Post by Mark Phelps on 2014-09-04
>  Can that be done without getting the device to connect to the os? 

NO -- the OS has to be able to see it in order for you to mount it and access the filesystem on it.

---

