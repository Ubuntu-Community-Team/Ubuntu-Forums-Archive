---
title: "Dell D830 - DVD Drive not working!"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by hokage on 2008-03-24
Brand new Dell D830 with factory DVD burner. DVD Burner is recognized but works only as a CDROM drive (not even DVD drive!). Really strange.
Here's what I found on dmesg, lshal, ecc.:

dmesg | grep -i dvd
[   19.074217] ata4.00: ATAPI: Optierg DVD+/-VW$AD-5560E $ $ $ $ $ $ $, DD51$ $, max UDMA/33
[   19.126323] scsi 3:0:0:0: CD-ROM            Ottmavc$ DVD/-VW$AD-5560E DD15 PQ: 0 ANSI: 5


lshal | grep -i dvd
  scsi.model = 'DVD/-VW$AD-5560E'  (string)
udi = '/org/freedesktop/Hal/devices/storage_model_DVD/_VW_AD_5560E'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_DVD/_VW_AD_5560E'  (string)

UBUNTU VERSION: Gutsy and Hardy

---

