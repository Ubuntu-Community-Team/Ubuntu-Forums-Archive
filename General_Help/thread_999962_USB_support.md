---
title: "USB support"
date: 2008-12-02
forum: General Help
---

### Post by shariefbe on 2008-12-02
Hello..i am new to linux....which driver is used to work the general USB port?which is core module to make work the USB port?help me please

---

### Post by Titan8990 on 2008-12-02
```
jordan@einstein:~$ lsmod | grep usb
usb_storage            73024  1 
libusual               18320  1 usb_storage
ide_core              116932  3 ide_cd,usb_storage,atiixp
usbcore               138760  5 usb_storage,libusual,ehci_hcd,ohci_hcd
scsi_mod              146828  6 sbp2,sg,sd_mod,usb_storage,3w_xxxx,libata

```


usbcore is defiantly needed, not sure about the others. USB should work "out of the box" fine.

---

### Post by shariefbe on 2008-12-02
what about this ehci_hcd,uhci_hcd?

---

### Post by Titan8990 on 2008-12-02
They are both used by usbcore but I couldn't tell you if they are required. I would experiment with loading/unloading the module.

---

### Post by shariefbe on 2009-10-18
Sorry for digging the old thread. As the required drivers for make the USB to support is "usbcore and host drivers"..Is it right? if its right mean i want to know why this "usb-skeleton.c" is used?

---

