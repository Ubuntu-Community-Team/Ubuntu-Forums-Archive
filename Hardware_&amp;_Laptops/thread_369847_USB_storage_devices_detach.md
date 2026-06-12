---
title: "USB storage devices detach"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by AllBuntu on 2007-02-25
Hey all,

I have found drivers to use USB storage failing big time on Ubuntu on two laptops and one server, on dapper 606.LTS and 6.10 Edgy. No good.

I define working when I can plug in a USB hard drive and read or write my favoruite 200 GiB file set without errors. Ubuntu errors out within minutes.

I have tried copying USB device 1 to USB device 2, or just reading from one USB device. Here is an excerpt dmesg:
[17683742.644000] kjournald starting.  Commit interval 5 seconds
[17683772.756000] usb 1-8: reset high speed USB device using ehci_hcd and address 10
[17683772.868000] usb 1-8: device descriptor read/64, error -71
[17683773.084000] usb 1-8: device descriptor read/64, error -71
[17683773.300000] usb 1-8: reset high speed USB device using ehci_hcd and address 10
[17683773.412000] usb 1-8: device descriptor read/64, error -71
[17683773.628000] usb 1-8: device descriptor read/64, error -71
[17683773.844000] usb 1-8: reset high speed USB device using ehci_hcd and address 10
[17683774.252000] usb 1-8: device not accepting address 10, error -71
[17683774.364000] usb 1-8: reset high speed USB device using ehci_hcd and address 10
[17683774.772000] usb 1-8: device not accepting address 10, error -71
[17683774.772000] usb 1-8: USB disconnect, address 10
[17683774.772000] sd 3:0:0:0: scsi: Device offlined - not ready after error recovery
[17683774.776000] sd 3:0:0:0: SCSI error: return code = 0x10000
[17683774.776000] end_request: I/O error, dev sdc, sector 63
[17683774.776000] Buffer I/O error on device sdc1, logical block 0
[17683774.776000] lost page write due to I/O error on sdc1

a. Result is that USB device ends up read-only with errors in its file system.
b. I have tried three make/models of USB devices, both USB-powered and self-powered.
c. I never had a problem in Windows. It also works on OS X but oh so slooow.

Note: You can not hotplug one USB device while you are accessing another (that would be hot hotplugging to me) Don't even try.

Q1. Are the USB drivers for Linux just plain out crappy as in fact-of-life?
Q2. Is there a way to fix or troubleshoot this other than wait?

This is an issue to me because I live off these huge SATA drives that only can connect to laptops over USB. If this does not work, I will have to resort to ssh over GbE which is plenty slow. SATA is a raw 300 MiB/s throttled by your bus architecture, USB is 20 MiB/s while ssh snoozes around something like 3 MiB/s.

Grateful for any suggestions,

Harald

---

### Post by yabbadabbadont on 2007-02-25
Make sure that the drives have been jumpered to Master.

---

### Post by AllBuntu on 2007-03-03
Actually, drive controllers that take power from the USB port are not reliable. I guess Windows either ignore the error or do a retry, while Linux refuses the drive alltoether.

I bought two self-powered enclosures (that self-power also the controller chip) and had no problems. Even when plugging a device during access of another.

---

