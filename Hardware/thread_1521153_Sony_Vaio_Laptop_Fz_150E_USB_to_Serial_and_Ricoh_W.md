---
title: "Sony Vaio Laptop Fz 150E USB to Serial and Ricoh Webcam"
date: 2010-06-30
forum: Hardware
---

### Post by TaimurK on 2010-06-30
Hi,
I just installed 10.4 LTS, everything installed without any problems, I am having Problems detecting my usb to serial Cable Pl 2303 and Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 R5U870, I used the upgrade firmware option on the webcam but it was of no use, The usb serial was detected once but after that I keep getting errors on $lsusb I dont know what to do can anyone please help? My $lsusb output :
$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


$dmesg
125.512079] hub 6-0:1.0: unable to enumerate USB device on port 1
[  166.608061] usb 6-1: new full speed USB device using uhci_hcd and address 18
[  166.728100] usb 6-1: device descriptor read/64, error -71
[  166.952086] usb 6-1: device descriptor read/64, error -71
[  167.168109] usb 6-1: new full speed USB device using uhci_hcd and address 19
[  167.288086] usb 6-1: device descriptor read/64, error -71
[  167.512073] usb 6-1: device descriptor read/64, error -71
[  167.728090] usb 6-1: new full speed USB device using uhci_hcd and address 20
[  168.136057] usb 6-1: device not accepting address 20, error -71
[  168.248081] usb 6-1: new full speed USB device using uhci_hcd and address 21
[  168.656107] usb 6-1: device not accepting address 21, error -71
[  168.656132] hub 6-0:1.0: unable to enumerate USB device on port 1
[  171.336073] usb 6-1: new full speed USB device using uhci_hcd and address 22
[  171.456058] usb 6-1: device descriptor read/64, error -71
[  171.680139] usb 6-1: device descriptor read/64, error -71
[  171.896085] usb 6-1: new full speed USB device using uhci_hcd and address 23
[  172.016110] usb 6-1: device descriptor read/64, error -71
[  172.240082] usb 6-1: device descriptor read/64, error -71
[  172.456098] usb 6-1: new full speed USB device using uhci_hcd and address 24
[  172.864095] usb 6-1: device not accepting address 24, error -71
[  172.976085] usb 6-1: new full speed USB device using uhci_hcd and address 25
[  173.384062] usb 6-1: device not accepting address 25, error -71
[  173.384086] hub 6-0:1.0: unable to enumerate USB device on port 1

-----------------------------------------------------------------------------------------------

15.111489] Linux video capture interface: v2.00
[   15.115583] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1837)
[   15.116307] input: UVC Camera (05ca:1837) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input9
[   15.116446] usbcore: registered new interface driver uvcvideo
[   15.116880] USB Video Class driver (v0.1.0)
[   15.216498] usb 6-1: device descriptor read/64, error -71

Some output omitted.
Thanks in Advance

---

### Post by aircooledbusnut on 2010-09-03
Try disconnecting the power, including the battery for thirty minutes.  This fixed my webcam issue and my other usb enumeration problems.

Hope it helps.

Clint

---

