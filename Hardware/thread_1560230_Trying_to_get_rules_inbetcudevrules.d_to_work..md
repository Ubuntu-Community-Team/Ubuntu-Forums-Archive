---
title: "Trying to get rules inb/etc/udev/rules.d to work."
date: 2010-08-24
forum: Hardware
---

### Post by patejam on 2010-08-24
I've been trying to get a rule to work so that when I plug in my USB mouse it will run a script that will turn the trackpad on/off. The script works perfectly when run in terminal.

Here's the output of udevadm info -q all -n /dev/input/mouse1. mouse1 is the mouse in question.

```

P: /devices/pci0000:00/0000:00:04.0/usb2/2-3/2-3:1.0/input/input13/mouse1
N: input/mouse1
S: char/13:33
S: input/by-id/usb-Logitech_USB_Receiver-mouse
S: input/by-path/pci-0000:00:04.0-usb-0:3:1.0-mouse
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:04.0/usb2/2-3/2-3:1.0/input/input13/mouse1
E: MAJOR=13
E: MINOR=33
E: DEVNAME=/dev/input/mouse1
E: SUBSYSTEM=input
E: ID_VENDOR=Logitech
E: ID_VENDOR_ENC=Logitech
E: ID_VENDOR_ID=046d
E: ID_MODEL=USB_Receiver
E: ID_MODEL_ENC=USB\x20Receiver
E: ID_MODEL_ID=c521
E: ID_REVISION=5700
E: ID_SERIAL=Logitech_USB_Receiver
E: ID_TYPE=hid
E: ID_BUS=usb
E: ID_USB_INTERFACES=:030102:030000:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=usbhid
E: ID_CLASS=mouse
E: ID_PATH=pci-0000:00:04.0-usb-0:3:1.0
E: DEVLINKS=/dev/char/13:33 /dev/input/by-id/usb-Logitech_USB_Receiver-mouse /dev/input/by-path/pci-0000:00:04.0-usb-0:3:1.0-mouse

```

Here's what I've ended up with for a file which I have named usb.rules

```

ACTION=="add", SUBSYSTEM=="input", RUN+="/bin/ms.pl"
ACTION=="remove", SUBSYSTEM=="input", RUN+="/bin/ms.pl"

```

I've tried adding and changing a few things to it, but I'm sure I'm missing something big.

---

