---
title: "PCMCIA USB 2.0 adapter problem"
date: 2010-02-25
forum: Hardware
---

### Post by cabelas on 2010-02-25
hi all

i have problem with my as-pmu24-v PCMCIA USB 2.0 adapter. i have to use this device, but it isn't work with external hdd at all. maybe i need to change **/sys/module/scsi_mod/parameters/inq_timeout** ? but i don't sure how to do it properly. 

lspci:
```
06:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
06:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
06:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
```

dmesg after connect hdd:
```
4288.200092] usb 3-1: device descriptor read/64, error -110
[ 4288.416115] usb 3-1: new full speed USB device using uhci_hcd and address 24
[ 4304.072118] usb 3-1: device descriptor read/64, error -110
[ 4319.944090] usb 3-1: device descriptor read/64, error -110
[ 4320.160149] usb 3-1: new full speed USB device using uhci_hcd and address 25
[ 4330.700082] usb 3-1: device not accepting address 25, error -110
[ 4330.812101] usb 3-1: new full speed USB device using uhci_hcd and address 26
[ 4341.364085] usb 3-1: device not accepting address 26, error -110
[ 4341.364140] hub 3-0:1.0: unable to enumerate USB device on port 1
```

---

