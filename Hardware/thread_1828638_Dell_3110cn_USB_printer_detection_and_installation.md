---
title: "Dell 3110cn USB printer detection and installation"
date: 2011-08-19
forum: Hardware
---

### Post by tuathan on 2011-08-19
Hi,

I've got a Dell 3110cn USB printer connected and running Ubuntu 9.10.
I am having problems getting Ubuntu to install the printer.

/var/log/messages shows that the printer is connected ok:

```

Aug 19 12:02:48 tuathan11 kernel: [  426.750022] usb 2-4: new high speed USB device using ehci_hcd and address 7
Aug 19 12:02:48 tuathan11 kernel: [  426.900907] usb 2-4: configuration #1 chosen from 1 choice
Aug 19 12:02:48 tuathan11 kernel: [  426.902117] usblp0: USB Bidirectional printer dev 7 if 0 alt 0 proto 2 vid 0x413C pid 0x5605
Aug 19 12:02:49 tuathan11 kernel: [  428.098412] usb 2-4: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

```


however the output of lsusb is:

```

Bus 006 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 1058:1102 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Also CUPS does not seem to detect that the printer is connected...

Can anyone help? Thanks.

---

