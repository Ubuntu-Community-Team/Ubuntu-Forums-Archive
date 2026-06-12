---
title: "Microdia webcam is not detected by lsusb"
date: 2009-07-01
forum: Hardware
---

### Post by szantaii on 2009-07-01
Hi!

I have a Lenovo 3000 N100 0768-BNG laptop with a built-in Microdia webcam. There is already a buildable kernel module, but I can't use it until the system detects the webcam. So my problem is that lsusb won't list the webcam, basically the system (Ubuntu 9.04 Jaunty Jackalope 32bit) doesn't recognize/detect it.
Here are some [FONT="Courier New"][SIZE="2"]lsusb[/SIZE][/FONT] and [FONT="Courier New"][SIZE="2"]dmesg[/SIZE][/FONT] outputs that might help solving the problem:
```
[FONT="Courier New"][SIZE="2"]$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 046d:c51b Logitech, Inc. 
Bus 002 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
```
```
[FONT="Courier New"][SIZE="2"]$ dmesg | grep usb
[    0.821936] usbcore: registered new interface driver usbfs
[    0.821936] usbcore: registered new interface driver hub
[    0.821936] usbcore: registered new device driver usb
[    3.288150] usb usb1: configuration #1 chosen from 1 choice
[    3.288738] usb usb2: configuration #1 chosen from 1 choice
[    3.289200] usb usb3: configuration #1 chosen from 1 choice
[    3.289674] usb usb4: configuration #1 chosen from 1 choice
[    3.290143] usb usb5: configuration #1 chosen from 1 choice
[    3.953024] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    4.129747] usb 2-2: configuration #1 chosen from 1 choice
[    4.368135] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    4.488064] usb 3-2: device descriptor read/64, error -71
[    4.712067] usb 3-2: device descriptor read/64, error -71
[    4.928043] usb 3-2: new full speed USB device using uhci_hcd and address 3
[    5.048070] usb 3-2: device descriptor read/64, error -71
[    5.272069] usb 3-2: device descriptor read/64, error -71
[    5.488043] usb 3-2: new full speed USB device using uhci_hcd and address 4
[    5.896066] usb 3-2: device not accepting address 4, error -71
[    6.008061] usb 3-2: new full speed USB device using uhci_hcd and address 5
[    6.416061] usb 3-2: device not accepting address 5, error -71
[   10.741342] usbcore: registered new interface driver btusb
[   16.700074] usb 3-2: new full speed USB device using uhci_hcd and address 6
[   16.820066] usb 3-2: device descriptor read/64, error -71
[   17.044070] usb 3-2: device descriptor read/64, error -71
[   17.260018] usb 3-2: new full speed USB device using uhci_hcd and address 7
[   17.388024] usb 3-2: device descriptor read/64, error -71
[   17.612068] usb 3-2: device descriptor read/64, error -71
[   17.828072] usb 3-2: new full speed USB device using uhci_hcd and address 8
[   18.252020] usb 3-2: device not accepting address 8, error -71
[   18.420039] usb 3-2: new full speed USB device using uhci_hcd and address 9
[   18.832012] usb 3-2: device not accepting address 9, error -71
[   51.728035] usb 2-1: new low speed USB device using uhci_hcd and address 3
[   51.904159] usb 2-1: configuration #1 chosen from 1 choice
[   51.965248] usbcore: registered new interface driver hiddev
[   51.984390] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input8
[   52.016166] generic-usb 0003:046D:C51B.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1/input0
[   52.029770] generic-usb 0003:046D:C51B.0002: hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1/input1
[   52.029796] usbcore: registered new interface driver usbhid
[   52.029800] usbhid: v2.6:USB HID core driver
[   73.296120] usb 3-2: new full speed USB device using uhci_hcd and address 10
[   73.416117] usb 3-2: device descriptor read/64, error -71
[   73.640118] usb 3-2: device descriptor read/64, error -71
[   73.859841] usb 3-2: new full speed USB device using uhci_hcd and address 11
[   73.980119] usb 3-2: device descriptor read/64, error -71
[   74.204118] usb 3-2: device descriptor read/64, error -71
[   74.420119] usb 3-2: new full speed USB device using uhci_hcd and address 12
[   74.832113] usb 3-2: device not accepting address 12, error -71
[   74.944119] usb 3-2: new full speed USB device using uhci_hcd and address 13
[   75.360103] usb 3-2: device not accepting address 13, error -71
[   84.720197] usb 2-1: USB disconnect, address 3
[   97.608163] usb 2-1: new low speed USB device using uhci_hcd and address 4
[   97.785297] usb 2-1: configuration #1 chosen from 1 choice
[   97.816074] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input9
[   97.834303] generic-usb 0003:046D:C51B.0003: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1/input0
[   97.851818] generic-usb 0003:046D:C51B.0004: hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1/input1
[  103.712180] usb 3-2: new full speed USB device using uhci_hcd and address 14
[  103.832157] usb 3-2: device descriptor read/64, error -71
[  104.056178] usb 3-2: device descriptor read/64, error -71
[  104.272153] usb 3-2: new full speed USB device using uhci_hcd and address 15
[  104.392157] usb 3-2: device descriptor read/64, error -71
[  104.616179] usb 3-2: device descriptor read/64, error -71
[  104.832161] usb 3-2: new full speed USB device using uhci_hcd and address 16
[  105.248170] usb 3-2: device not accepting address 16, error -71
[  105.360161] usb 3-2: new full speed USB device using uhci_hcd and address 17
[  105.776167] usb 3-2: device not accepting address 17, error -71
[  192.000175] usb 3-2: new full speed USB device using uhci_hcd and address 18
[  192.120157] usb 3-2: device descriptor read/64, error -71
[  192.344318] usb 3-2: device descriptor read/64, error -71
[  192.560192] usb 3-2: new full speed USB device using uhci_hcd and address 19
[  192.680160] usb 3-2: device descriptor read/64, error -71
[  192.904195] usb 3-2: device descriptor read/64, error -71
[  193.120177] usb 3-2: new full speed USB device using uhci_hcd and address 20
[  193.528126] usb 3-2: device not accepting address 20, error -71
[  193.640152] usb 3-2: new full speed USB device using uhci_hcd and address 21
[  194.056212] usb 3-2: device not accepting address 21, error -71
[  197.808215] usb 2-1: USB disconnect, address 4
[  201.636156] usb 3-2: new full speed USB device using uhci_hcd and address 22
[  201.756139] usb 3-2: device descriptor read/64, error -71
[  201.980126] usb 3-2: device descriptor read/64, error -71
[  202.196176] usb 3-2: new full speed USB device using uhci_hcd and address 23
[  202.316177] usb 3-2: device descriptor read/64, error -71
[  202.540166] usb 3-2: device descriptor read/64, error -71
[  202.756084] usb 3-2: new full speed USB device using uhci_hcd and address 24
[  203.164214] usb 3-2: device not accepting address 24, error -71
[  203.276387] usb 3-2: new full speed USB device using uhci_hcd and address 25
[  203.692105] usb 3-2: device not accepting address 25, error -71
[  246.908039] usb 2-1: new low speed USB device using uhci_hcd and address 5
[  247.140374] usb 2-1: configuration #1 chosen from 1 choice
[  247.166555] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input10
[  247.192162] generic-usb 0003:046D:C51B.0005: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1/input0
[  247.209457] generic-usb 0003:046D:C51B.0006: hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1/input1
[  781.148159] usb 3-2: new full speed USB device using uhci_hcd and address 26
[  781.355193] usb 3-2: not running at top speed; connect to a high speed hub
[  781.394919] usb 3-2: configuration #1 chosen from 1 choice
[  797.736420] usb 3-2: USB disconnect, address 26[/SIZE][/FONT]
```
I also attached a full [FONT="Courier New"][SIZE="2"]lshw[/SIZE][/FONT] output.
Please help me if you can, any ideas will be appreciated. Thanks in advance.

---

### Post by Irtsi on 2009-11-19
I have the same laptop and exactly the same problem. Webcam worked properly with previous versions of ubuntu and even on xubuntu 9.10. But ubuntu 9.10 does not recognize it at all.

---

