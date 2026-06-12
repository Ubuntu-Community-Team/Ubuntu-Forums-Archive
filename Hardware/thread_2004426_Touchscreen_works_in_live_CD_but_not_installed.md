---
title: "Touchscreen works in live CD but not installed"
date: 2012-06-15
forum: Hardware
---

### Post by redxine on 2012-06-15
I have a few Planar PT1510MX's.  They seem completely identical, however the newest one has a completely different USB vendor ID:

PT1510MX (newer one):
```
Bus 003 Device 004: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
```

PT1510MX (working):
```
Bus 003 Device 005: ID 0637:0001
```

The newest touch screen works flawlessly from the live CD, with perfect calibration, and the two older monitors require calibration, but work as expected.  However once the system (Xubuntu) is installed only the 0637:0001 device continues to work.  The D-WAV hardware behaves very strangely, as clicking on one point will result in a different mouse click everytime (as if the baud rate is wrong).

dmesg reveals slightly different messages between the live and installed system, however I can't seem to work out how to solve this problem:

Live system (working):
```
[ 5437.064058] usb 3-1: new full-speed USB device number 6 using uhci_hcd
[ 5437.231504] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input27
[ 5437.233074] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input28
[ 5437.233237] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input29
[ 5437.233320] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input30
[ 5437.233453] generic-usb 0003:0EEF:0001.0008: input,hiddev0,hidraw2: USB HID v2.10 Pointer [eGalax Inc. USB TouchController] on usb-0000:00:1d.1-1/input0
```

Installed system (not working):
```
    [27549.232014] usb 2-1: new full-speed USB device number 7 using ohci_hcd
    [27549.417999] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input19
    [27549.418325] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input20
    [27549.420490] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input21
    [27549.420599] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input22
    [27549.420773] generic-usb 0003:0EEF:0001.0004: input,hiddev0,hidraw1: USB HID v2.10 Pointer [eGalax Inc. USB TouchController] on usb-0000:00:13.0-1/input0
```

I noticed the uhci_hcd/ohci_hcd difference, but am besides myself as to what it means or how to fix it.  Any suggestions?


Update:
A reboot appears to have solved the problem.  Will update if problem reappears.
```
[  221.876030] usb 4-2: new full-speed USB device number 5 using uhci_hcd
[  222.044277] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input14
[  222.047249] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input15
[  222.047402] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input16
[  222.047481] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input17
[  222.047606] generic-usb 0003:0EEF:0001.0004: input,hiddev0,hidraw2: USB HID v2.10 Pointer [eGalax Inc. USB TouchController] on usb-0000:00:1d.2-2/input0
```

---

