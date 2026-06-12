---
title: "ubuntu 18.04 + logitech m195 wireless receiver freezing from time to time"
date: 2019-08-18
forum: Hardware
---

### Post by Pitero on 2019-08-18
Hi,

I'm using ubuntu 18.04 with logitech m195 with wireless receiver. Previously I had problems with with usb 2.0 as mouse was freezing from time to time (when friezed there was no option to restore).

I tried different things, in particular turning off automatic usb suspend and updating to new kernels incl. the newest 5.2.8 which were expected to fix some problems with logitech wireless support. Nothing helped. Mouse worked correctly only with usb 3.0 port.

However after the latest packages updates from ubuntu the disease touched also usb 3.0 port. Mouse freezes from time to time. The only difference is that with usb2.0 there was no option to unfreeze, while now with usb 3.0 port sometimes this freeze is permanent and sometimes mouse start working after few seconds.

When mouse works ok I have the following info from

```

dmesg |tail
```

```
[ 2283.457180] usb 1-1: New USB device found, idVendor=046d, idProduct=c52f, bcdDevice=22.00
[ 2283.457185] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2283.457188] usb 1-1: Product: USB Receiver
[ 2283.457190] usb 1-1: Manufacturer: Logitech
[ 2283.462208] logitech-djreceiver 0003:046D:C52F.000B: hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:14.0-1/input0
[ 2283.520670] logitech-djreceiver 0003:046D:C52F.000C: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-1/input1
[ 2283.581118] logitech-djreceiver 0003:046D:C52F.000C: device of type eQUAD step 4 DJ (0x04) connected on slot 1
[ 2283.603126] logitech-hidpp-device 0003:046D:1020.000D: HID++ 1.0 device connected.
[ 2283.665531] input: Logitech M215 as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.1/0003:046D:C52F.000C/0003:046D:1020.000D/input/input29
[ 2283.666073] logitech-hidpp-device 0003:046D:1020.000D: input,hidraw3: USB HID v1.11 Mouse [Logitech M215] on usb-0000:00:14.0-1/input1:1

```

However during freeze I have the following message

```
[ 2316.618497] usb 1-1: new full-speed USB device number 38 using xhci_hcd
[ 2316.618684] usb 1-1: Device not responding to setup address.
[ 2316.826685] usb 1-1: Device not responding to setup address.
[ 2317.034490] usb 1-1: device not accepting address 38, error -71
[ 2317.034572] usb usb1-port1: unable to enumerate USB device
[ 2330.822456] usb 1-1: new full-speed USB device number 39 using xhci_hcd
[ 2330.950397] usb 1-1: device descriptor read/64, error -71
[ 2331.186507] usb 1-1: device descriptor read/64, error -71
[ 2331.422451] usb 1-1: new full-speed USB device number 40 using xhci_hcd
[ 2331.550497] usb 1-1: device descriptor read/64, error -71

```

Any help would be more than appreciated. :)

---

