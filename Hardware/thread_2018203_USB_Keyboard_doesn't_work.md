---
title: "USB Keyboard doesn't work"
date: 2012-07-06
forum: Hardware
---

### Post by palimmo on 2012-07-06
Hello. A few days ago I bought a SL640 Hama USB keyboard to use on my laptop with Ubuntu 12.04. 
But I'm having problems, as it works one time out of 10! 
While on my girlfriend's laptop, with Win Vista, always works. 

Here are some infos:

```
~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
Bus 006 Device 003: ID 04d9:1503 Holtek Semiconductor, Inc. Shortboard Lefty
```

As you can see, the OS recognized it but the keyboard doesn't react  ... even the Caps Lock and Num Lock keys don't blink.
Regarding the legacy support (useful for GRUB), I have found no entry in the BIOS. But I'm not interested in it. I just want to use it in Ubuntu.
Help.

Thank you!

---

### Post by palimmo on 2012-07-06
Well.. on the same laptop I have Win7 in dual boot. And I have to say that it always works on it.
In GRUB it works sometimes.
Surprisingly now I have booted my laptop: the usb keyboard hasn't worked in GRUB but it has worked since the ubuntu login! And now I'm typing with it.
:confused:
```
~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
Bus 006 Device 004: ID 04d9:1503 Holtek Semiconductor, Inc. Shortboard Lefty

```

So..potentially it works. And that's good. But I can't work in this situation. What should I do?
Thanks.
Ale

---

### Post by palimmo on 2012-07-06
Well.. it means that Ubuntu has the right drivers and they work. But how to "load" them always correctly?

---

### Post by palimmo on 2012-07-06
Here a dmesg when it works
[http://pastebin.ubuntu.com/1077873/](http://pastebin.ubuntu.com/1077873/)

---

### Post by palimmo on 2012-07-06
Another example.
After several plug/unplug actions, now it works.

Here ***dmesg***:
```
[ 1007.280090] usb 6-1: USB disconnect, device number 19
[ 1010.192060] usb 5-2: new low-speed USB device number 20 using uhci_hcd
[ 1010.732051] usb 5-2: device not accepting address 20, error -84
[ 1010.844046] usb 5-2: new low-speed USB device number 21 using uhci_hcd
[ 1011.133123] usb 5-2: can't set config #1, error -84
[ 1029.848104] usb 5-2: USB disconnect, device number 21
[ 1038.064057] usb 4-2: new low-speed USB device number 4 using uhci_hcd
[ 1038.363131] usb 4-2: can't set config #1, error -84
[ 1089.120105] usb 4-2: USB disconnect, device number 4
[ 1096.460073] usb 6-1: new low-speed USB device number 20 using uhci_hcd
[ 1097.060046] usb 6-1: device not accepting address 20, error -71
[ 1097.172077] usb 6-1: new low-speed USB device number 21 using uhci_hcd
[ 1097.534131] generic-usb: probe of 0003:04D9:1503.0016 failed with error -84
[ 1097.554110] generic-usb: probe of 0003:04D9:1503.0017 failed with error -32
[ 1140.952075] usb 6-1: USB disconnect, device number 21
[ 1145.968084] usb 6-1: new low-speed USB device number 22 using uhci_hcd
[ 1146.512052] usb 6-1: device not accepting address 22, error -71
[ 1146.624087] usb 6-1: new low-speed USB device number 23 using uhci_hcd
[ 1146.957109] generic-usb: probe of 0003:04D9:1503.0018 failed with error -84
[ 1147.000116] generic-usb: probe of 0003:04D9:1503.0019 failed with error -84
[ 1199.480080] usb 6-1: USB disconnect, device number 23
[ 1201.928080] usb 5-2: new low-speed USB device number 22 using uhci_hcd
[ 1202.301173] generic-usb: probe of 0003:04D9:1503.001A failed with error -84
[ 1202.342182] generic-usb: probe of 0003:04D9:1503.001B failed with error -84
[ 1227.008092] usb 5-2: USB disconnect, device number 22
[ 1234.416066] usb 4-2: new low-speed USB device number 5 using uhci_hcd
[ 1234.960058] usb 4-2: device not accepting address 5, error -71
[ 1235.072071] usb 4-2: new low-speed USB device number 6 using uhci_hcd
[ 1235.616071] usb 4-2: device not accepting address 6, error -84
[ 1235.728071] usb 4-2: new low-speed USB device number 7 using uhci_hcd
[ 1235.903088] usb 4-2: can't set config #1, error -84
[ 1258.256080] usb 4-2: USB disconnect, device number 7
[ 1265.796058] usb 5-2: new low-speed USB device number 23 using uhci_hcd
[ 1266.388076] usb 5-2: device not accepting address 23, error -71
[ 1266.500074] usb 5-2: new low-speed USB device number 24 using uhci_hcd
[ 1266.793126] usb 5-2: can't set config #1, error -84
[ 1333.152111] usb 5-2: USB disconnect, device number 24
[ 1336.520066] usb 6-1: new low-speed USB device number 24 using uhci_hcd
[ 1336.805091] usb 6-1: can't set config #1, error -84
[ 1402.592088] usb 6-1: USB disconnect, device number 24
[ 1406.020078] usb 5-2: new low-speed USB device number 25 using uhci_hcd
[ 1406.299121] usb 5-2: can't set config #1, error -84
[ 1564.288095] usb 5-2: USB disconnect, device number 25
[ 1566.968105] usb 6-1: new low-speed USB device number 25 using uhci_hcd
[ 1567.508073] usb 6-1: device not accepting address 25, error -71
[ 1567.620073] usb 6-1: new low-speed USB device number 26 using uhci_hcd
[ 1568.164069] usb 6-1: device not accepting address 26, error -84
[ 1568.276085] usb 6-1: new low-speed USB device number 27 using uhci_hcd
[ 1568.326126] usb 6-1: device descriptor read/all, error -84
[ 1568.440071] usb 6-1: new low-speed USB device number 28 using uhci_hcd
[ 1568.651128] usb 6-1: can't set config #1, error -84
[ 1649.848120] usb 6-1: USB disconnect, device number 28
[ 1653.104073] usb 5-2: new low-speed USB device number 26 using uhci_hcd
[ 1653.462591] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input17
[ 1653.462767] generic-usb 0003:04D9:1503.001C: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.0-2/input0
[ 1653.552194] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.1/input/input18
[ 1653.552337] generic-usb 0003:04D9:1503.001D: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.0-2/input1

```

How can I solve it?

---

### Post by palimmo on 2012-07-07
No idea?

---

### Post by palimmo on 2012-07-08
bump :confused:

---

### Post by palimmo on 2012-07-12
[-(

---

