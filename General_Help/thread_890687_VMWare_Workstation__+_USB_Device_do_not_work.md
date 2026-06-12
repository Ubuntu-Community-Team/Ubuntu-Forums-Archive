---
title: "VMWare Workstation  + USB Device do not work"
date: 2008-08-15
forum: General Help
---

### Post by fahadsadah on 2008-08-15
I plug a phone in, but VMWare can't use it. Seems to be common to all kernels above 2.6.20 ([http://communities.vmware.com/thread/83464?tstart=0&start=0](http://communities.vmware.com/thread/83464?tstart=0&start=0)).
Full info:
Relevant bit of lsusb
```
Bus 004 Device 006: ID 22b8:4902 Motorola PCS Triplet GSM Phone (AT)
```

Relevant chunk of dmesg
```
[ 1133.070887] usb 4-1: new full speed USB device using uhci_hcd and address 5
[ 1133.190750] usb 4-1: device descriptor read/64, error -71
[ 1133.415498] usb 4-1: device descriptor read/64, error -71
[ 1133.630262] usb 4-1: new full speed USB device using uhci_hcd and address 6
[ 1133.830064] usb 4-1: configuration #1 chosen from 1 choice
[ 1133.840154] cdc_acm 4-1:1.0: ttyACM0: USB ACM device
```

VMWare message on connection
```
The specified device appears to be claimed by another driver (cdc_acm) on the host operating system which means that the device may be in use. To continue, the device will first be disconnected from its current driver.
```

VMWare error message
```
VMware workstation was unable to claim the device (No such file or directory)
```

I hope I've provided enough info

---

### Post by fahadsadah on 2008-08-15
UPDATE

I have just set the phone to use usbserial_generic rather than cdc_acm on the host.

No change

---

### Post by patdurling on 2008-10-15
It looks like you will need to punch some holes into your firewall. See the below web page:

[http://www.clydesdalesoftware.net/blogs/jluif/CommentView,guid,68e0498d-afca-4cc1-88b2-c0afc5c2c68e.aspx](http://www.clydesdalesoftware.net/blogs/jluif/CommentView,guid,68e0498d-afca-4cc1-88b2-c0afc5c2c68e.aspx)

---

