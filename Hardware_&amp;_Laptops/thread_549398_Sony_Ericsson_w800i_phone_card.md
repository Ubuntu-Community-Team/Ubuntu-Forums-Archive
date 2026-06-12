---
title: "Sony Ericsson w800i phone card"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by megamaced on 2007-09-12
Hello!

I have a Sony Ericsson w800i mobile phone. When I used Dapper Drake and plugged the phone into the USB port, the memory stick would be instantly recognised and I could transfer files. I recently installed a fresh copy of Gusty Gibbon and applied all updates and the phone is not getting detected anymore. I get the following output after running dmesg:

```
[ 5370.588378] usb 4-1: new full speed USB device using uhci_hcd and address 2
[ 5370.712071] usb 4-1: device descriptor read/64, error -71
[ 5370.939548] usb 4-1: device descriptor read/64, error -71
[ 5371.155057] usb 4-1: new full speed USB device using uhci_hcd and address 3
[ 5371.274780] usb 4-1: device descriptor read/64, error -71
[ 5371.498267] usb 4-1: device descriptor read/64, error -71
[ 5371.713772] usb 4-1: new full speed USB device using uhci_hcd and address 4
[ 5372.120837] usb 4-1: device not accepting address 4, error -71
[ 5372.232591] usb 4-1: new full speed USB device using uhci_hcd and address 5
[ 5372.639649] usb 4-1: device not accepting address 5, error -71
[ 5381.547255] usb 4-1: new full speed USB device using uhci_hcd and address 6
[ 5381.670961] usb 4-1: device descriptor read/64, error -71
[ 5381.898441] usb 4-1: device descriptor read/64, error -71
[ 5382.113946] usb 4-1: new full speed USB device using uhci_hcd and address 7
[ 5382.233668] usb 4-1: device descriptor read/64, error -71
[ 5382.457164] usb 4-1: device descriptor read/64, error -71
[ 5382.672669] usb 4-1: new full speed USB device using uhci_hcd and address 8
[ 5383.079738] usb 4-1: device not accepting address 8, error -71
[ 5383.191481] usb 4-1: new full speed USB device using uhci_hcd and address 9
[ 5383.598526] usb 4-1: device not accepting address 9, error -71
```

What can I do to resolve this?

Thanks

---

### Post by Impotence on 2008-06-10
Sup Megamaced, fancy seeing you here! (this thread is the first hit for "ubuntu usb w800i"

Have you had any luck with your phone? My w800i works as long as i mount it manually with -t vfat (KDE4 remix, mounts other USB storage, fat and NTFS, automatically)

---

