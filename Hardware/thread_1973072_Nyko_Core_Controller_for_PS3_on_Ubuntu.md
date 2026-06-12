---
title: "Nyko Core Controller for PS3 on Ubuntu"
date: 2012-05-04
forum: Hardware
---

### Post by joedoe4 on 2012-05-04
hey guys :), I recently bought a wired ps3 controller so that I could use to play a few games on my dell inspirion but upon connecting it I just get four blinking lights. From what I understand most ps3 controllers when wired will "just work" when plugged in. However when I ran dmesg I get a couple of strange things. 

```
[    0.746313] usbcore: registered new interface driver usbfs
[    0.746329] usbcore: registered new interface driver hub
[    0.746354] usbcore: registered new device driver usb
[    1.052217] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.052308] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.070653] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.070832] hub 1-0:1.0: USB hub found
[    1.070975] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.090612] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.090770] hub 2-0:1.0: USB hub found
[    1.090830] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.090842] uhci_hcd: USB Universal Host Controller Interface driver
[    1.090884] usbcore: registered new interface driver libusual
[    1.382055] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.515120] hub 1-1:1.0: USB hub found
[    1.625659] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.758221] hub 2-1:1.0: USB hub found
[    1.829391] usb 1-1.4: new high-speed USB device number 3 using ehci_hcd
[    2.032955] usb 1-1.5: new high-speed USB device number 4 using ehci_hcd
[    2.391468] usbcore: registered new interface driver uas
[    2.391504] Initializing USB Mass Storage driver...
[    2.391568] usbcore: registered new interface driver usb-storage
[    2.391571] USB Mass Storage support registered.
[    2.460166] usb 2-1.1: new full-speed USB device number 3 using ehci_hcd
[    2.510889] scsi6 : usb-storage 1-1.5:1.0
[    2.511044] usbcore: registered new interface driver ums-realtek
[    2.651747] usb 2-1.2: new low-speed USB device number 4 using ehci_hcd
[    2.748738] usb 1-1.5: USB disconnect, device number 4
[    2.752900] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5
[    2.753091] generic-usb 0003:15D9:0A4C.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1d.0-1.2/input0
[    2.753105] usbcore: registered new interface driver usbhid
[    2.753107] usbhid: USB HID core driver
[   21.115122] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   21.115397] usbcore: registered new interface driver btusb
[   21.380062] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input9
[   21.380280] usbcore: registered new interface driver uvcvideo
[   21.380283] USB Video Class driver (1.1.1)
[ 6577.624940] usb 2-1.3: new full-speed USB device number 5 using ehci_hcd
[ 6577.718878] usb 2-1.3: unable to read config index 0 descriptor/start: -32
[ 6577.718884] usb 2-1.3: chopping to 0 config(s)
[ 6577.720367] usb 2-1.3: string descriptor 0 read error: -32
[ 6577.720555] usb 2-1.3: no configuration chosen from 0 choices
[ 6892.702838] usb 2-1.3: USB disconnect, device number 5
[ 6899.288365] usb 2-1.3: new full-speed USB device number 6 using ehci_hcd
[ 6899.360221] usb 2-1.3: device descriptor read/64, error -32
[ 6899.535864] usb 2-1.3: device descriptor read/64, error -32
[ 6899.711520] usb 2-1.3: new full-speed USB device number 7 using ehci_hcd

```

---

