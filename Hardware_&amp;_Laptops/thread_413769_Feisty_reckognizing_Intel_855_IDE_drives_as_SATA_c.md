---
title: "Feisty reckognizing Intel 855 IDE drives as SATA causing huge problems"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by Gromit83 on 2007-04-19
I have a huge problem. Feisty reckognizes my IDE drive on my Aopen 1557 Laptop as a SCSI/S-ATA hard drive, so when Feisty tries to boot. It all crashes at GRUB who gives wrong command to my drive when booting so im like :confused: 

The Drive is a Samsung 2,5" ATA 5400RPM 80GB Drive with a Intel 855PM motherboard with a Radeon Mobility 9700 128 MB graphicsboard.

---

### Post by patrickfromspain on 2007-04-19
If you have upgraded, I'd try a fresh install. ATA drives use now the SATA stuff and are called the same way, that's normal. It's a change in kernel 2.6.20 and will remain the same.

---

### Post by misse- on 2007-08-15
This causes an even more huge problem of mine. My IDE-disk is recognized as SCSI, which when trying to boot xen causes huge problems as XEN recognizes them as IDE disks and can't find any sda drives..

I know the error in this case seems to lie in Xen configuration, but even so. Does anyone have any suggestion on how to make xen either recognize them as sda or how to change them to hda's?

---

