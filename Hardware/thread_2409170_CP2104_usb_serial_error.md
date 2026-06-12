---
title: "CP2104 usb serial error"
date: 2018-12-28
forum: Hardware
---

### Post by warddr-8 on 2018-12-28
Hello everyone

I am struggeling for 2 days already to get a device working on linux.
It uses a CP2104 usb serial converter.

Every time I plug it in I get this error on dmesg:
```
[ 4498.679808] usb 2-1.3: USB disconnect, device number 21
[ 4498.680069] cp210x 2-1.3:1.0: device disconnected
[ 4498.904811] usb 2-1.3: new full-speed USB device number 23 using ehci-pci
[ 4499.400932] usb 2-1.3: device not accepting address 23, error -32
[ 4501.973109] usb 2-1.3: new full-speed USB device number 25 using ehci-pci
[ 4502.085109] usb 2-1.3: New USB device found, idVendor=10c4, idProduct=ea60
[ 4502.085117] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 4502.085122] usb 2-1.3: Product: CP2104 USB to UART Bridge Controller
[ 4502.085127] usb 2-1.3: Manufacturer: Silicon Labs
[ 4502.085131] usb 2-1.3: SerialNumber: 017F858F
[ 4502.086252] cp210x 2-1.3:1.0: cp210x converter detected
[ 4502.087636] cp210x ttyUSB0: failed set request 0x3 status: -32
[ 4502.087661] cp210x: probe of ttyUSB0 failed with error -32
```

What I already tried:
-Googling, I found some mentions of similar problems, but never a solution
-On my windows pc it works fine, so the hardware itself works fine
-I asked a friend to try it on their linux pc: same error
-I tried it with a manjaro livecd, to test it with an entirely diffirent flavor of linux: same error
-I tried diffirent USB ports and diffirent USB cables to make sure: same error

Anyone any suggestions for what I could try?

---

### Post by Autodave on 2018-12-28
How about telling us what the device is?  That may help.  Also, did the device come with a Windows driver?  A Windows install disk?

---

### Post by him610 on 2018-12-28
Is this the device you are referring to...[https://www.pololu.com/product/1308]("https://www.pololu.com/product/1308")
Have you installed the driver yet?

---

### Post by warddr-8 on 2018-12-29
It is this device:
[https://blog.hackster.io/the-ttgo-t-beam-an-esp32-lora-board-d44b08f18628](https://blog.hackster.io/the-ttgo-t-beam-an-esp32-lora-board-d44b08f18628)
but the IC that does the USB - TTL is the same you found, and drivers should be the same.

All I could find is that the drivers should be installed by default.

---

