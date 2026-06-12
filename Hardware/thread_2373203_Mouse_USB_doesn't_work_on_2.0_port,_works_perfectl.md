---
title: "Mouse USB doesn't work on 2.0 port, works perfectly on 3.0 port"
date: 2017-10-03
forum: Hardware
---

### Post by janadestiny on 2017-10-03
Hello everyone, 
I've just installed Ubuntu recently, alongside with Windows 10. Everything works perfectly at first, but after I installed Steam and a Steam game to play on Ubuntu, things started to go wrong (I uinstalled Steam, but that didn't help). My USB began freeze sometimes, and eventually not work anymore. If I plug it in my USB 2.0 ports, it doesn't move (but lsusb still recognizes it). And if I plug it in a USB 3.0 port, it works like magic! Can anyone help me with this problem?
- Any mouse plug in 2.0 port doesn't work
- 2.0 ports still recognize my USB
- My mouse works fine on my friend's computer 

Here is my lsusb result with **2.0 port**
```
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader ControllerBus 001 Device 006: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 003: ID 0c45:6a04 Microdia 
Bus 001 Device 059: ID 192f:0916 Avago Technologies, Pte. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
And here is **3.0 port**
```
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader ControllerBus 001 Device 006: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 003: ID 0c45:6a04 Microdia 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 012: ID 192f:0916 Avago Technologies, Pte. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
And a part of my dmesg on **2.0 port**
```
[ 7932.248385] usb 1-1.2: Product: USB Optical Mouse[ 7932.251301] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:192F:0916.0016/input/input32
[ 7932.251588] hid-generic 0003:192F:0916.0016: input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1.2/input0
[ 7949.576206] usb 1-1.2: USB disconnect, device number 59
[ 7953.383030] usb 2-1: new low-speed USB device number 12 using xhci_hcd
[ 7953.525913] usb 2-1: New USB device found, idVendor=192f, idProduct=0916
[ 7953.525916] usb 2-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[ 7953.525917] usb 2-1: Product: USB Optical Mouse
[ 7953.529060] input: USB Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/0003:192F:0916.0017/input/input33
[ 7953.591347] hid-generic 0003:192F:0916.0017: input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:14.0-1/input0
[ 8106.270000] usb 2-1: USB disconnect, device number 12
[ 8108.135541] usb 1-1.2: new low-speed USB device number 60 using ehci-pci
[ 8108.247432] usb 1-1.2: New USB device found, idVendor=192f, idProduct=0916
[ 8108.247437] usb 1-1.2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[ 8108.247440] usb 1-1.2: Product: USB Optical Mouse
[ 8108.250316] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:192F:0916.0018/input/input34
[ 8108.307862] hid-generic 0003:192F:0916.0018: input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1.2/input0

``` 

My Ubuntu version is 16.04.3 LTS and my laptop is Dell Inspiron 15.

---

