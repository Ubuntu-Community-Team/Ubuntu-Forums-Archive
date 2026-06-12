---
title: "headset not working"
date: 2010-11-13
forum: Hardware
---

### Post by mrsray on 2010-11-13
Hello everyone

I have  a dsp 500 plantronics headset.  I am on 10.04 and can't seem to get the darn thing to be recognized.

lsusb only shows my keyboard and mouse.  Testing the usb port the headset was plugged into with a flash drive, the flash drive shows up ...

chris@chris-desktop:~$ lsusb
Bus 002 Device 007: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 002: ID 04ca:0027 Lite-On Technology Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
chris@chris-desktop:~$ lsusb
Bus  002 Device 008: ID 13fe:1f00 Kingston Technology Company Inc.  DataTraveler 2.0 4GB Flash Drive / Patriot Xporter 32GB (PEF32GUSB)  Flash Drive
Bus 002 Device 007: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 002: ID 04ca:0027 Lite-On Technology Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


dmesg | grep usb  gives me lots of errors but still no headset (plugged in) ...
[    0.386300] usbcore: registered new interface driver usbfs
[    0.386310] usbcore: registered new interface driver hub
[    0.386329] usbcore: registered new device driver usb
[    0.450115] usb usb1: configuration #1 chosen from 1 choice
[    0.512068] usb usb2: configuration #1 chosen from 1 choice
[    1.230015] usb 2-5: new low speed USB device using ohci_hcd and address 2
[    1.459085] usb 2-5: configuration #1 chosen from 1 choice
[    1.469558] usbcore: registered new interface driver hiddev
[    1.476272] input: Lite-On Technology Corp. USB Multimedia Keyboard as /devices/pci0000:00/0000:00:0a.0/usb2/2-5/2-5:1.0/input/input3
[    1.476340] generic-usb 0003:04CA:0027.0001: input,hidraw0: USB HID v1.10 Keyboard [Lite-On Technology Corp. USB Multimedia Keyboard] on usb-0000:00:0a.0-5/input0
[    1.491086] input: Lite-On Technology Corp. USB Multimedia Keyboard as /devices/pci0000:00/0000:00:0a.0/usb2/2-5/2-5:1.1/input/input4
[    1.491155] generic-usb 0003:04CA:0027.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [Lite-On Technology Corp. USB Multimedia Keyboard] on usb-0000:00:0a.0-5/input1
[    1.491169] usbcore: registered new interface driver usbhid
[    1.491172] usbhid: v2.6:USB HID core driver
[    1.800014] usb 2-9: new full speed USB device using ohci_hcd and address 3
[    2.027037] usb 2-9: device descriptor read/all, error -84
[    2.210011] usb 2-9: new full speed USB device using ohci_hcd and address 4
[    2.427039] usb 2-9: device descriptor read/all, error -84
[    2.610019] usb 2-9: new full speed USB device using ohci_hcd and address 5
[    2.657039] usb 2-9: device descriptor read/all, error -71
[    2.841956] usb 2-9: new full speed USB device using ohci_hcd and address 6
[    2.890039] usb 2-9: device descriptor read/all, error -84
[    3.240024] usb 2-10: new low speed USB device using ohci_hcd and address 7
[    3.468114] usb 2-10: configuration #1 chosen from 1 choice
[    3.480364] input: Logitech Trackball as /devices/pci0000:00/0000:00:0a.0/usb2/2-10/2-10:1.0/input/input5
[    3.480431] generic-usb 0003:046D:C404.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:0a.0-10/input0
[ 9843.735288] usb 1-9: new high speed USB device using ehci_hcd and address 5
[ 9843.950037] usb 1-9: device descriptor read/64, error -71
[ 9844.273309] usb 1-9: device descriptor read/64, error -71
[ 9844.502534] usb 1-9: new high speed USB device using ehci_hcd and address 6
[ 9844.712916] usb 1-9: device descriptor read/64, error -71
[ 9845.040032] usb 1-9: device descriptor read/64, error -71
[ 9845.266184] usb 1-9: new high speed USB device using ehci_hcd and address 7
[ 9845.743091] usb 1-9: device not accepting address 7, error -71
[ 9845.862666] usb 1-9: new high speed USB device using ehci_hcd and address 8
[ 9846.344245] usb 1-9: device not accepting address 8, error -71
[ 9846.890033] usb 2-9: new full speed USB device using ohci_hcd and address 8
[ 9847.104050] usb 2-9: not running at top speed; connect to a high speed hub
[ 9847.128140] usb 2-9: configuration #1 chosen from 1 choice
[ 9847.235432] usbcore: registered new interface driver usb-storage
[ 9847.237002] usb-storage: device found at 8
[ 9847.237004] usb-storage: waiting for device to settle before scanning
[ 9852.234096] usb-storage: device scan complete
[ 9873.876046] usb 2-9: USB disconnect, address 8
[ 9895.992576] usb 2-9: new full speed USB device using ohci_hcd and address 9
[ 9896.211055] usb 2-9: device descriptor read/all, error -71
[ 9896.395345] usb 2-9: new full speed USB device using ohci_hcd and address 10
[ 9896.611055] usb 2-9: device descriptor read/all, error -84
[ 9896.792572] usb 2-9: new full speed USB device using ohci_hcd and address 11
[ 9896.840057] usb 2-9: device descriptor read/all, error -71
[ 9897.030026] usb 2-9: new full speed USB device using ohci_hcd and address 12
[ 9897.071056] usb 2-9: device descriptor read/all, error -71
[13983.805142] usb 2-9: new full speed USB device using ohci_hcd and address 13
[13984.020056] usb 2-9: device descriptor read/all, error -84
[13984.206116] usb 2-9: new full speed USB device using ohci_hcd and address 14
[13984.420054] usb 2-9: device descriptor read/all, error -84
[13984.610034] usb 2-9: new full speed USB device using ohci_hcd and address 15
[13984.660053] usb 2-9: device descriptor read/all, error -84
[13984.842532] usb 2-9: new full speed USB device using ohci_hcd and address 16
[13984.890053] usb 2-9: device descriptor read/all, error -84

I have skype installed that I would like to use my headset on.

Any suggestions?   :confused:

thanks in advance

ps, the headset is tested and working on windows

---

