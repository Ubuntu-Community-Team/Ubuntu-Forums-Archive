---
title: "usb keyboard not working ubuntu 11.10"
date: 2012-01-03
forum: Hardware
---

### Post by jendicott on 2012-01-03
I installed ubuntu on my T500 laptop a couple of days ago and everything was working fine. Today I plugged a usb keyboard and mouse directly into 2 of the usb ports. I then powered up. Everything was fine during the boot process I used the usb keyboard to select the boot option first in the windows - ubuntu choice and then in grub to move between the options and select one. When I am presented with the login prompt i use the usb keyboard to enter the password and that works as expected. When i try to use the usb keyboard anytime after that it doesn't do anything. The laptop keyboard works fine and the usb mouse works.

In searching the forums I found lots of usb problems described but my situation seems too be a little different. Reading the man pages there was a suggestion that it might be possible to add an entry to /etc/modules for ukbd but that doesn't appear to make any difference.

when I run dmesg | grep usb I get:

[    0.376092] usbcore: registered new interface driver hub
[    0.376116] usbcore: registered new device driver usb
[    1.292058] usb 4-1: new full speed USB device number 2 using uhci_hcd
[    1.704074] usb 6-1: new low speed USB device number 2 using uhci_hcd
[    2.136075] usb 6-2: new low speed USB device number 3 using uhci_hcd
[    9.359375] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input4
[    9.360947] generic-usb 0003:045E:00CB.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:1d.0-1/input0
[    9.377378] input: Microsoft Wired Keyboard 600 as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input5
[    9.377530] generic-usb 0003:045E:0750.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Wired Keyboard 600] on usb-0000:00:1d.0-2/input0
[    9.408334] input: Microsoft Wired Keyboard 600 as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.1/input/input6
[    9.408476] generic-usb 0003:045E:0750.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Wired Keyboard 600] on usb-0000:00:1d.0-2/input1
[    9.408513] usbcore: registered new interface driver usbhid
[    9.408516] usbhid: USB HID core driver

when I do: /etc$ lsusb

I get:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 006 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 006 Device 003: ID 045e:0750 Microsoft Corp. Wired Keyboard 600

So it looks like the device is recognized and there but it is ignored.

Any suggestions would be greatly appreciated.

---

### Post by Mark Phelps on 2012-01-05
One thing you could try is booting the laptop without the keyboard connected.  Once Ubuntu is up a running, THEN plugin the keyboard.

Hoping that, like Windows, Ubuntu will detect the "new" device and install the proper drivers for it.

---

### Post by jendicott on 2012-01-05
> **Mark Phelps said:**
> One thing you could try is booting the laptop without the keyboard connected.  Once Ubuntu is up a running, THEN plugin the keyboard.

Hoping that, like Windows, Ubuntu will detect the "new" device and install the proper drivers for it.

Thanks. That works. Disables the laptop keyboard as well.:D

---

### Post by swissz on 2013-01-09
Hi!
I am having the same problem on my desktop and not just my keyboard but my mouse is also doing the same. Unfortunately, I am bound to this Ubuntu version, so an update is not a viable solution.
Is there any other solution for this problem than plugging and unplugging the keyboard and the mouse all the time?
Regards,
Swissz

---

