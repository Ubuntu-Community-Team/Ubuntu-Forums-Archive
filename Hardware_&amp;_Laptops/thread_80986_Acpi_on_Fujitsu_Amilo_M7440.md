---
title: "Acpi on Fujitsu Amilo M7440"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by Manolito on 2005-10-23
Hello ppl ! 

Ubuntu is an excellent distribution ! It's the first time I've ever installed Linux and everything runs smoothly !

Though, I'm not sure if my acpi features are correctly installed. I've got sound, i can change the display brightness & the battery indicator is working accurately. Are those indications that everything is all right ?

Furthermore, how can I check if DMA is enabled for my CD-ROM drive ? I tried burning an audio CD & it took very long (4x approximately).

Thanks in advance

---

### Post by maher on 2005-10-26
In the ubuntu (breezy) default kernel configuration there is an option which you should disable:

Device Drivers --->  ATA/ATAPI/MFM/RLL support  ---> [ ] Enable DMA only for disks 

recompile you kernel and see if there is a difference.

---

