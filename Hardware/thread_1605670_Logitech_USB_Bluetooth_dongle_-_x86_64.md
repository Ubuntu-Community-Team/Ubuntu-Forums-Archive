---
title: "Logitech USB Bluetooth dongle - x86_64"
date: 2010-10-25
forum: Hardware
---

### Post by FettsVett on 2010-10-25
My Logitech bluetooth dongle isn't being detected as a Bluetooth device.

```
fettsvett@Windu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:5112 Dell Computer Corp. Photo AIO Printer 924
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 017: ID 046d:c70c Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 001 Device 016: ID 046d:c70b Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 001 Device 015: ID 046d:0b02 Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 001 Device 006: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 001 Device 004: ID 0424:2602 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 0424:2512 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

they specifically state HID proxy mode. 

This receiver did work in 10.04 32-bit.

If you need any logs, let me know.

---

### Post by FettsVett on 2010-10-26
Well, I've gotten it working by tinkering around, however it's a temporary fix...

I had to remove the 'KERNEL' rules from the /lib/udev/rules.d/70-hid2hci.rules file

```
ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[35e]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[4abc]|c71[34bc]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
```

This will obviously be overwritten when I upgrade udev, so it would probably make sense to figure out where the problem is so I can submit a bug report to the proper project.

---

