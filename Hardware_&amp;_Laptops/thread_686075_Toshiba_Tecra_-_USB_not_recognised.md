---
title: "Toshiba Tecra - USB not recognised"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by DR. John Iscar on 2008-02-02
Hello,
I am running the latest ubuntu 7.10 on my notebook and all works well except the USB ports. I am using one for the mouse but I cannot install a web cam as ubuntu does not see any USB ports. I am also running Innotek and it also does not see any USB ports either as I suspect that is because ubuntu has not installed the drivers?

Any suggestions and help would be greatly appreciated.

Many thanks, Chris.

---

### Post by Yellow Pasque on 2008-02-02
Hi Chris. First, Check obvious things like seeing if there any USB settings in the BIOS or seeing if there's a BIOS update that fixes USB issues. What kind of notebook do you have?
Also, if you could provide output from a few commands:
```
sudo update-pciids
lspci
```&
```
lsmod | grep usb
```
Try connecting a USB device and seeing if it's recognized with:
```
lsusb
```

---

### Post by DR. John Iscar on 2008-02-03
Hello,
Many thanks for the feedback and the attached text file has all  the output from your comments.

Chris

---

### Post by Yellow Pasque on 2008-02-03
The drivers are loaded properly and ubuntu sees the devices.

---

