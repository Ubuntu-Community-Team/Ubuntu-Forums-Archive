---
title: "Downgrade USB3 to USB2"
date: 2013-11-28
forum: Hardware
---

### Post by odror on 2013-11-28
OS. UBUNTU 13.10 64bit

I Suspect that the the xhci module is not properly working on my computer. Unfortunately this driver controls also all my USB2 ports as well.

1. Is it possible to force disabling of the xhci module and use the ehci module. Will USB3 port work as USB2.

2. Is it possible to force USB2 ports only to use the ehci module  instead of the xhci driver.


Thanks

---

### Post by linux4me on 2013-12-17
I ran across your thread while trying to find some more information on [my XHCI problem]("http://ubuntuforums.org/showthread.php?t=2194155").

In that thread, you will see that my (hopefully temporary) workaround was to disable XHCI in my BIOS. Take a look in your BIOS for some entry that controls XHCI. For me, it was "XHCI mode," which I just set to "disabled." Now, EHCI is used, and speeds are USB 2.0 speeds. 

I believe your USB 3.0 ports are backward-compatible with USB 2.0 and USB 1.0, so you should be okay until this gets fixed.

---

### Post by odror on 2013-12-17
> **linux4me said:**
> I ran across your thread while trying to find some more information on [my XHCI problem]("http://ubuntuforums.org/showthread.php?t=2194155").

In that thread, you will see that my (hopefully temporary) workaround was to disable XHCI in my BIOS. Take a look in your BIOS for some entry that controls XHCI. For me, it was "XHCI mode," which I just set to "disabled." Now, EHCI is used, and speeds are USB 2.0 speeds. 

I believe your USB 3.0 ports are backward-compatible with USB 2.0 and USB 1.0, so you should be okay until this gets fixed.

I will check it again, but I do not think that I have this setting in my BIOS. I have an HP computer (using MSI MB). Also in Ububntu 13.10 the xhci module is included in the kernel. It is not a loadable module. (I cannot blacklist it).

---

### Post by linux4me on 2013-12-17
Okay. Good luck.

I misread your post. I think unless you disable it somehow, XHCI is going to be used for USB 2.0 ports too. It superceded EHCI. The way to find out would be to plug a USB 3.0 device into a USB 2.0 port and then run:
```
dmesg
```
in Terminal to see whether it's using XHCI or EHCI.

---

### Post by odror on 2013-12-17
> **linux4me said:**
> Okay. Good luck.

I misread your post. I think unless you disable it somehow, XHCI is going to be used for USB 2.0 ports too. It superceded EHCI. The way to find out would be to plug a USB 3.0 device into a USB 2.0 port and then run:
```
dmesg
```
in Terminal to see whether it's using XHCI or EHCI.

The kernel is loading the xhci modules to all the visible USB ports regardless whether  it is 2.0 or 3.0. The ehci is also loaded, but it is used by an "invisible" hub.

> $ lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/14p, 480M
    |__ Port 1: Dev 2, If 0, Class=Vendor Specific Class, Driver=asix, 480M
    |__ Port 2: Dev 98, If 0, Class=Vendor Specific Class, Driver=hdpvr, 480M
    |__ Port 3: Dev 4, If 0, Class=Vendor Specific Class, Driver=mceusb, 12M
    |__ Port 3: Dev 4, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 9: Dev 6, If 0, Class=Human Interface Device, Driver=, 12M
    |__ Port 11: Dev 7, If 0, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 13: Dev 8, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 13: Dev 8, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 14: Dev 9, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 14: Dev 9, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 14: Dev 9, If 2, Class=Human Interface Device, Driver=usbhid, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M


---

### Post by linux4me on 2013-12-17
That's what I was afraid of. I guess XHCI needs to be disabled in the BIOS. 

I'm reading a [Launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1050352") that may be related.

---

### Post by linux4me on 2013-12-17
That's what I was afraid of. I guess XHCI needs to be disabled in the BIOS. 

I'm reading a [Launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1050352") that may be related.

---

