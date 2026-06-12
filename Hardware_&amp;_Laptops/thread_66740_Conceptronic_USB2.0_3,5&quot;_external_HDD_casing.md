---
title: "Conceptronic USB2.0 3,5&quot; external HDD casing"
date: 2005-09-18
forum: Hardware &amp; Laptops
---

### Post by novaflash on 2005-09-18
It simply won't be recognized. I have a computer with USB 1.1 ports, and I checked to make sure this drive is backwards compatible with USB 1.1. It definitely is. I don't know why it's not being recognized and I would like to try some things to see if it might have been 'discovered' as a USB device but that Ubuntu didn't know what to do with it. If anyone has a solution, that'd be great ofcourse ;)

Here's some more info on the situation;

When I plug a USB flash disk in, it's recognized by Ubuntu and the contents shown in a new window on the Ubuntu desktop. That works as expected, aside from the write to USB disk issue, but that's another story. This test just proves that the USB port is working. When I run tail -s 3 -f /var/log/messages I get some nice results telling me that USB flash disk has been found and that the module sd_mod was loaded successfully. When I unplug the flash drive I get a USB disconnect message. All works fine. But when I plug the conceptronic external USB drive in, nothing happens. When I unplug it, nothing happens.

Suggestions? Ideas?

---

### Post by gstrock on 2005-09-22
I just tried an ADS external case and the USB hookup  doesn't work either.
The drive shows up under usbviewer and dmesg shows the system is trying:
usb-storage: device found at 2
usb 4-2: reset high speed USB device using ehci_hcd and address 2
scsi: Device offlined - not ready after error recovery: host 0 channel 0 id 0 lun 0
usb-storage: device scan complete

and that's all she wrote!

a USB key works just fine.  Nautilus automatically opens when it's inserted.

---

