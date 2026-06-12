---
title: "IOGEAR Hard Drive"
date: 2005-12-25
forum: Hardware &amp; Laptops
---

### Post by .Justin on 2005-12-25
I have a IOGEAR Hard Drive:

Vendor: WDC WD20
Model: 00JB-00GVA0
Rev: 08.0

And it is not supported by default.

Anytime I reboot the computer/want to use the device, I must run the command:

> echo 'WDC WD20:00JB-00GVA0:1' > /proc/scsi/device_info

To get the device to detect and auto-mount.

My question: Is there a way to get the device to auto-detect this line/setting on boot-up or just plain by default?

Thanks,
Justin.

---

### Post by .Justin on 2005-12-28
Any ideas anyone? I'll be setting up a dual boot soon but would like backup everything and keep it that way whenever I boot.

Thanks..

---

