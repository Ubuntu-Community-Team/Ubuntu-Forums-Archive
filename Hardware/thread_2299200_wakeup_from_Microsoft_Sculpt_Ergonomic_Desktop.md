---
title: "wakeup from Microsoft Sculpt Ergonomic Desktop"
date: 2015-10-16
forum: Hardware
---

### Post by coolman7 on 2015-10-16
I just bought a Microsoft Sculpt Ergonomic Desktop (L5V-00001) set. It includes a keyboard and a mouse. By default it worked for most features at  Ubuntu 14.04 out of the box. But there are some problems:
It wakes up with keyboard and mouse. But I want to disable wakeup with mouse, because it is too sensitive. my computer will wake up if I touch the table, mouse moves milimetric and it wakes up my computer.

```
# lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 13d3:5169 IMC Networks 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 007: ID 045e:07a5 Microsoft Corp. Wireless Receiver 1461C
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 8087:07da Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
# lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M
    |__ Port 3: Dev 2, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 3: Dev 2, If 1, Class=Wireless, Driver=btusb, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
        |__ Port 2: Dev 7, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 2: Dev 7, If 1, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 2: Dev 7, If 2, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 3: Dev 4, If 0, Class=Vendor Specific Class, Driver=rtsx_usb, 480M
        |__ Port 4: Dev 5, If 0, Class=Video, Driver=uvcvideo, 480M
        |__ Port 4: Dev 5, If 1, Class=Video, Driver=uvcvideo, 480M
```



I can enable and disable keyboard and mouse at the same time but I can't disable one of them. How can I enable disable one of them?

Another problem is some features are not working. for example mouse scroll wheel has another function: If you pull to left, means go back but not working. And some media keys are working some are not working.

---

### Post by Mike_Walsh on 2015-10-16
Not meaning to be funny here.....but why don't you just switch the mouse off when you're not using it?


Regards,

Mike. ;)

---

### Post by coolman7 on 2015-10-16
If I don't forget, I switch off until I will find a better way. For short time periods I prefer not to switch off the mouse.

---

### Post by Mike_Walsh on 2015-10-18
Well, another idea might just be to turn the mouse upside down when you're not actually using it..... Hey, I'm trying the simple suggestions here, first of all....!


Regards,

Mike. :D

---

### Post by coolman7 on 2015-10-18
Wow this is even better idea :)

I think this problem applies to other keyboard mouse combo sets. Most of them share single USB dongle (unifying or property). Wake up devices defined by usb ports. So I wonder is there any solution for this? Of course other than making mouse non functional :)

```
 cat /proc/acpi/wakeup Device    S-state      Status   Sysfs node
P0P1      S0    *disabled
EHC1      S3    *enabled   pci:0000:00:1d.0
EHC2      S3    *enabled   pci:0000:00:1a.0
XHC      S3    *enabled   pci:0000:00:14.0
HDEF      S0    *disabled  pci:0000:00:1b.0
PXSX      S3    *enabled   pci:0000:01:00.0
PXSX      S3    *disabled  pci:0000:02:00.0
PXSX      S3    *disabled
PXSX      S3    *disabled
RP05      S0    *disabled
PXSX      S3    *disabled
RP06      S0    *disabled
PXSX      S3    *disabled
RP07      S0    *disabled
PXSX      S3    *disabled
RP08      S0    *disabled
PXSX      S3    *disabled
PEG0      S4    *disabled
PEGP      S4    *disabled
PEG1      S4    *disabled
PEG2      S4    *disabled
PEG3      S4    *disabled
LID0      S3    *enabled   platform:PNP0C0D:00



```

---

### Post by tgalati4 on 2015-10-18
Can you disable wakeup-from-mouse in Windows?  Normally a BIOS setting allows you to disable wakeup from USB, but that would disable both devices since they are on one USB receiver.

You can try to turn off power to some USB ports by using *acpitool*.  But again since they communicate through one wireless USB receiver, that will end up turning both off.

---

### Post by coolman7 on 2015-10-18
I haven't tried it at windows. I haven't used windows for ages :)
Anyway if this is not possible because of technical limitations, there is only one solution: use two USB dongles, if possible and if you have enough usb ports. It should be possible for Logitech because of unifying. But Microsoft Sculpt Desktop set has pre-matched USB dongle. You can't get another dongle and match as unifying. No luck :)

---

### Post by tgalati4 on 2015-10-18
That was my thinking.  Use a wired mouse and just shut off the USB port on the wired mouse during S3 sleep.

---

