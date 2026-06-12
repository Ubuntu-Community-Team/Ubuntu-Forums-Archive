---
title: "Mounting iPhone inside VmWare"
date: 2010-06-21
forum: Hardware
---

### Post by gen0 on 2010-06-21
I have a Windows XP machine at work running Ubuntu 10.04 LTS as a *guest* in VmWare Workstation 7.1.

When I plug my iPhone into my PC, it's picked up by VmWare and "connected" to the Ubuntu 10.04 virtual machine.  However, I cannot see the iPhone filesystem in Nautilus.

When plugging in the iPhone, I get the following in /var/log/messages (within the Ubuntu guest):

```
Jun 21 20:49:18 ubuntu kernel: [  687.952590] usb 1-1: new high speed USB device using ehci_hcd and address 5
Jun 21 20:49:18 ubuntu kernel: [  688.109390] usb 1-1: configuration #1 chosen from 4 choices
```


And the device shows up in hal-device:

```
$ hal-device | grep iPhone
  info.product = 'iPhone 3GS'  (string)
  usb_device.product = 'iPhone 3GS'  (string)
```


And lsusb:

```
$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05ac:1294 Apple, Inc. iPhone 3GS
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


I also tried installing ifuse, but get the following error:

```
$ sudo ifuse /mnt/ipod/
No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.
```


I expected this to work right out of the box.  Can anyone think of any extra things I need to do to make this work inside a virtual machine?

---

### Post by gen0 on 2010-06-30
anyone?

---

### Post by chudder on 2010-07-16
From what I can see it looks like you have the reverse problem I do.  I have a Win7 vbox in Ubuntu.  I'm trying to mount the ipod in Win7.  Any clue how to do that?

---

