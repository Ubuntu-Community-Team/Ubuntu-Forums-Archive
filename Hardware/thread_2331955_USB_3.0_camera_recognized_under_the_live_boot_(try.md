---
title: "USB 3.0 camera recognized under the live boot (try Ubuntu) but not from HDD"
date: 2016-07-27
forum: Hardware
---

### Post by molinadavid on 2016-07-27
Hi all, I have a very weird (at least for me) problem, I am relatively new to Ubuntu and trying to install an Intel RealSense R200 camera under Ubuntu 14.04, I have already installed it and tested on my development pc under Ubuntu 16.04 but has not been able to do so on the 14.04 pc (different pc).

This camera works only with USB 3.0 and the pc I am having problems with only has one USB 3.0, now when I do a lsusb this is the result I get

```
Bus 004 Device 003: ID 08ff:168b AuthenTec, Inc. 
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 1bcf:288e Sunplus Innovation Technology Inc. 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0951:1665 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

and the result of lsusb -t
```
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
        |__ Port 5: Dev 3, If 0, Class=Vendor Specific Class, Driver=, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
        |__ Port 3: Dev 3, If 0, Class=Video, Driver=uvcvideo, 480M
        |__ Port 3: Dev 3, If 1, Class=Video, Driver=uvcvideo, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M
    |__ Port 3: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 480M

```

Now for the interesting part is that if I use an installation stick and choose the option of "try Ubuntu" the camera is listed under the devices
```
Bus 004 Device 003: ID 08ff:168b AuthenTec, Inc. 
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 1bcf:288e Sunplus Innovation Technology Inc. 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 8086:0a80 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0951:1665 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The camera in question is "Bus 002 Device 004: ID 8086:0a80 Intel Corp."

and again the lsusb -t
```
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
        |__ Port 5: Dev 3, If 0, Class=Vendor Specific Class, Driver=, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
        |__ Port 3: Dev 3, If 0, Class=Video, Driver=uvcvideo, 480M
        |__ Port 3: Dev 3, If 1, Class=Video, Driver=uvcvideo, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
    |__ Port 1: Dev 4, If 0, Class=Video, Driver=uvcvideo, 5000M
    |__ Port 1: Dev 4, If 1, Class=Video, Driver=uvcvideo, 5000M
    |__ Port 1: Dev 4, If 2, Class=Video, Driver=uvcvideo, 5000M
    |__ Port 1: Dev 4, If 3, Class=Video, Driver=uvcvideo, 5000M
    |__ Port 1: Dev 4, If 4, Class=Video, Driver=uvcvideo, 5000M
    |__ Port 1: Dev 4, If 5, Class=Video, Driver=uvcvideo, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M
    |__ Port 3: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 480M

```

I tried reinstalling everything, updating the Kernel for 4.4 but nothing works so far, I would be very happy if any one could point me on the right direction.

---

### Post by molinadavid on 2016-07-28
strange update: I just re installed (yet again) Ubuntu 14.04, at the beginning nothing changed, however when I boot the pc with one of the USB sticks plugged I can now see the camera

```

Bus 002 Device 003: ID 08ff:168b AuthenTec, Inc.
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:288e Sunplus Innovation Technology Inc.
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 8086:0a80 Intel Corp.
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 056e:6022 Elecom Co., Ltd
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

But it only happens if that particular USB stick is plugged (Elecom Co.Ltd) and the machine is booted with the USB stick and the camera plugged.

---

