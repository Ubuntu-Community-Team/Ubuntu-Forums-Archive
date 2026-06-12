---
title: "blacklisting usb driver doesn't work (for when i plug in ipod)"
date: 2008-12-04
forum: Hardware
---

### Post by 77bridge on 2008-12-04
How can I blacklist the 'usb_storage' (or usb-storage) module so that it does not start up when I plug in my iPod?

I've tried the approach described here: [HOWTO: Prevent (blacklist) modules from loading but that hasn't worked. ]("http://ubuntuforums.org/showthread.php?t=166624") (ubuntuforums.org/showthread.php?t=166624)

For example, when I restart and I execute: 'lsmod | grep usb' I get the following output:
usbhid 32128 0
hid 38784 1 usbhid
usbcore 146412 5 uvcvideo,usbhid,ehci_hcd,uhci_hcd

That's ok. Now when I plug in my iPod, I execute the same command and I get the following output:
usb_storage 73664 0
libusual 19108 1 usb_storage
usbhid 32128 0
hid 38784 1 usbhid
scsi_mod 151436 6 usb_storage,sbp2,sr_mod,sg,sd_mod,libata
usbcore 146412 7 usb_storage,libusual,uvcvideo,usbhid,ehci_hcd,uhci _hcd

usb_storage is the very first module listed, yet my /etc/modprobe.d/blacklist and /etc/modprobe.d/blacklist-custom files both have the following lines:
blacklist usb-storage
blacklist usb_storage

So that's my question: how can I actually blacklist usb_storage so that it doesn't start up when I plug in my iPod?

Thanks!!!

---

