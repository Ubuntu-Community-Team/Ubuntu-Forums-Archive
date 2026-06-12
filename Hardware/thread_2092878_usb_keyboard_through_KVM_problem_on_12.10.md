---
title: "usb keyboard through KVM problem on 12.10"
date: 2012-12-09
forum: Hardware
---

### Post by AdrianPtchv on 2012-12-09
Hi people,

After the ubuntu 12.10 ugrade my usb keyboard does not work.
It is connected through a KVM switch and worked flawlessly before the upgrade.
Now it works only if connected directly to the PC.

here's lsusb result with keyboard connected directly to the PC:

> lsusb
Bus 001 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 004 Device 002: ID 085c:0300 ColorVision, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 056a:0069 Wacom Co., Ltd Bamboo One
[COLOR="Plum"]Bus 002 Device 003: ID 09da:0260 A4 Tech Co., Ltd [/COLOR] -- this is the keyboard


and here's when connected through the KVM:

> lsusb
Bus 001 Device 004: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 004 Device 002: ID 085c:0300 ColorVision, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 056a:0069 Wacom Co., Ltd Bamboo One


Additional info:

The keyboard itself has an USB hub incorporated (apart from this it is absolutely generic one).

Once I was able to get it working through the KVM - I booted up with the keyboard in the PC directly and then plugged it in the KVM and it worked.
After restart worked again.
After second restart it didn't. And it is like this ever since.

The keyboard still works on the other machine on the KVM - not upgraded Ubuntu.

The keyboard works during boot and for GRUB. It stops once the Ubuntu login screen is displayed.


Ideas will be greatly appreciated. :)
Thanks in advance!

---

### Post by AdrianPtchv on 2012-12-10
No one with similar peoblem or solution?

---

### Post by AdrianPtchv on 2012-12-11
A bit of additional info: it _might_ has something to do with a problem with Ubuntu 12.10 and the handling of usb devices - sometimes when the keyboard is plugged directly in the PC the usb flash drives are not mounted properly.

---

### Post by AdrianPtchv on 2012-12-12
The problem has been resolved by plugging the KVM in USB hub first.

> lsusb
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 004 Device 002: ID 085c:0300 ColorVision, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 8054:0001  
Bus 001 Device 005: ID 056a:0069 Wacom Co., Ltd Bamboo One
Bus 001 Device 011: ID 1307:0330 Transcend Information, Inc. 63-in-1 Multi-Card Reader/Writer
Bus 001 Device 010: ID 09da:0260 A4 Tech Co., Ltd 
Bus 001 Device 007: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 008: ID 0d62:1000 Darfon Electronics Corp. 
Bus 001 Device 009: ID 058f:9410 Alcor Micro Corp. Keyboard

This is lsusb with the keyboard plugged in the KVM now.

It would be usefull if someone could explain this phenomenon.

---

### Post by heiko_s on 2013-01-29
I have also noticed an USB issue after the upgrade, which I believe is related.

My dmesg output shows an 8 second delay during boot followed by the message "usb_submit_urb(ctrl) failed: -1". See below:

```
[11.358067] usb 2-1.6.3: new low-speed USB device number 10 using ehci_hcd
[   11.455563] usb 2-1.6.3: New USB device found, idVendor=058f, idProduct=9410
[   11.455572] usb 2-1.6.3: New USB device strings: Mfr=0, Product=2, SerialNumber=3
[   11.455580] usb 2-1.6.3: Product: USB Multimedia Keyboard
[   11.455586] usb 2-1.6.3: SerialNumber: USB Multimedia Keyboard
[   19.601944] hid-generic 0003:058F:9410.0002: usb_submit_urb(ctrl) failed: -1
[   19.601974] hid-generic 0003:058F:9410.0002: timeout initializing reports
[   19.602132] input: USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/input/input3
[   19.602354] hid-generic 0003:058F:9410.0002: input,hidraw1: USB HID v1.10 Device [USB Multimedia Keyboard] on usb-0000:00:1a.0-1.6/input1
[   19.602638] input: USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.2/input/input4
[   19.602902] hid-generic 0003:058F:9410.0003: input,hidraw2: USB HID v1.10 Mouse [USB Multimedia Keyboard] on usb-0000:00:1a.0-1.6/input2
[   19.603272] input: Microsoft Wired Keyboard 600 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.1/2-1.6.1:1.0/input/input5

```

I'm using an Edimax KVM which may be the culprit here (maybe not the KVM itself, but the way Ubuntu 12.10 handles it). My keyboard is a Microsoft keyboard which is correctly identified earlier in the boot sequence:
```
[   11.105456] usb 2-1.6.1: New USB device found, idVendor=045e, idProduct=0750
[   11.105469] usb 2-1.6.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   11.105478] usb 2-1.6.1: Product: Wired Keyboard 600
[   11.105484] usb 2-1.6.1: Manufacturer: Microsoft

```

I'm running a Xen hypervisor and both ports of the KVM are connected to two different USB controllers on the PC: 0000:00:1d.0 and 0000:00:1a.0. During boot and while in the Linux dom0 environment the KVM is switched to 0000:00:1d.0. When running the Windows VM, USB controller 0000:00:1a.0 is passed through to Windows.

It looks like as if two different keyboards are identified during boot, although there is only one keyboard connected. Could be a KVM issue?

Somehow Linux sees a keyboard on 0000:00:1a.0 which is the KVM port that should be off.

Do you have the same or similar KVM - Edimax EK-2U2C 2 ports USB KVM switch?

P.S.: I didn't notice this issue with Ubuntu 12.04, at least not the boot delay.

---

