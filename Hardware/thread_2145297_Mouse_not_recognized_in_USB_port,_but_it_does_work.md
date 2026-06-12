---
title: "Mouse not recognized in USB port, but it does work through a hub in the same port"
date: 2013-05-15
forum: Hardware
---

### Post by lsolano on 2013-05-15
Hi:


(ubuntu 13.04)


If I connect my mouse in one USBv2 port on my laptop, it does not work. This is the output I get from dmesg:


```
usb 1-1.2: new full-speed USB device number 21 using ehci-pci
usb 1-1.2: device not accepting address 21, error -32
usb 1-1.2: new full-speed USB device number 22 using ehci-pci
usb 1-1.2: device not accepting address 22, error -32
hub 1-1:1.0: unable to enumerate USB device on port 2

```



Now, if I plug in a USB hub in that same port, I get:


```
usb 1-1.2: new high-speed USB device number 23 using ehci-pci
usb 1-1.2: New USB device found, idVendor=1a40, idProduct=0101
usb 1-1.2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
usb 1-1.2: Product: USB 2.0 Hub
hub 1-1.2:1.0: USB hub found
hub 1-1.2:1.0: 4 ports detected

```

and, if I now plug the mouse in one of the ports of the hub I get:


```
usb 1-1.2.1: new full-speed USB device number 24 using ehci-pci
usb 1-1.2.1: New USB device found, idVendor=4168, idProduct=1011
usb 1-1.2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
usb 1-1.2.1: Product: Targus Wireless Optical Mouse
usb 1-1.2.1: Manufacturer: reserved
input: reserved Targus Wireless Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1:1.0/input/input15
hid-generic 0003:4168:1011.0005: input,hiddev0,hidraw0: USB HID v1.11 Mouse [reserved Targus Wireless Optical Mouse] on usb-0000:00:1a.0-1.2.1/input0

```



and the mouse works perfectly.


Well, I hope I can make the mouse work directly in the port without the hub. 


Thanks in advance for any help!

---

