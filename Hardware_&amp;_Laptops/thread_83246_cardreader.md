---
title: "cardreader"
date: 2005-10-28
forum: Hardware &amp; Laptops
---

### Post by stoeptegel on 2005-10-28
I have an aerocool coolpanel with cardreader and some usb/sata/firewire ports in it. I want to try getting the cardreader working.

$ lsusb
```
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 0472:0065 Chicony Electronics Co., Ltd PFU-65 Keyboard
Bus 001 Device 004: ID 1532:0001
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp.
Bus 001 Device 002: ID 0472:0065 Chicony Electronics Co., Ltd PFU-65 Keyboard
Bus 001 Device 001: ID 0000:0000
```

$ lsmod | grep usb
```

usb_storage            64704  0
usbhid                 30688  0
usbcore               104188  5 usb_storage,usbhid,ehci_hcd,ohci_hcd
scsi_mod              124872  5 sr_mod,sbp2,usb_storage,sd_mod,libata
ide_core              125268  4 usb_storage,ide_cd,ide_generic,amd74xx
```

Can someone help me with this?

---

