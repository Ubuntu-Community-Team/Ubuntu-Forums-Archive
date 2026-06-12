---
title: "Asus AT5IONT-I and USB3"
date: 2011-10-12
forum: Hardware
---

### Post by Buuuh on 2011-10-12
I'm currently using the mentioned board, which supports usb3 on ubuntu 10.10 (latest updates are installed).
At the moment i have an usb3 hard drive and an usb3 hub, both are connected to the two blue usb-ports (this should be the usb3 ports).

Now the device managment tells me, that the usb3 drive is connected with 480MBit/s, which is just usb2.

lsusb shows me:
```

/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 1: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 1: Dev 2, If 0, Class=stor., Driver=usb-storage, 480M
    |__ Port 3: Dev 4, If 0, Class=stor., Driver=usb-storage, 480M
    |__ Port 7: Dev 6, If 0, Class=hub, Driver=hub/4p, 480M
        |__ Port 1: Dev 7, If 0, Class=vend., Driver=, 1.5M
        |__ Port 3: Dev 8, If 0, Class=vend., Driver=dvb_usb_vp7045, 480M
        |__ Port 4: Dev 9, If 0, Class=HID, Driver=usbhid, 1.5M
        |__ Port 4: Dev 9, If 1, Class=HID, Driver=usbhid, 1.5M

```The usb3 hard disk according to this is connected to bus 01 port 1. Bus 01 Port 7 is the usb3 hub. On Bus 01 port 3 is a usb2 drive.
You can see, that there is an usb3 controller (bus 06) but there are no devices connected. 

In the Bios are just options for usb2. 

Does anybody have an idea, what's wrong here? Of course i would like to use my hard disks with the maximum speed.

Edit: Removing all other devices, besides the usb3 hdd, from the bus didn't change anything.

---

