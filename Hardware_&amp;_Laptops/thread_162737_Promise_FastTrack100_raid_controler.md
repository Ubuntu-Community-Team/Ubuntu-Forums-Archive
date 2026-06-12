---
title: "Promise FastTrack100 raid controler???"
date: 2006-04-19
forum: Hardware &amp; Laptops
---

### Post by phlip_19 on 2006-04-19
I have a Promise FastTrack100 raidcontroler, and would like to use it on my ubuntu machine, but cant seem to get it to work...

$ fdisk /dev/hdg
device not found

$ sudo dmraid -r
ERROR: hpt37x: reading /dev/hde[Input/output error]
ERROR: hpt45x: reading /dev/hde[Input/output error]
ERROR: isw: reading /dev/hde[Input/output error]
ERROR: lsi: reading /dev/hde[Input/output error]
ERROR: nvidia: reading /dev/hde[Input/output error]
ERROR: pdc: reading /dev/hde[Input/output error]
ERROR: pdc: reading /dev/hde[Input/output error]
ERROR: pdc: reading /dev/hde[Input/output error]
ERROR: pdc: reading /dev/hde[Input/output error]
ERROR: pdc: reading /dev/hde[Input/output error]
ERROR: sil: reading /dev/hde[Input/output error]
ERROR: via: reading /dev/hde[Input/output error]
ERROR: hpt37x: reading /dev/hdg[Input/output error]
ERROR: hpt45x: reading /dev/hdg[Input/output error]
ERROR: isw: reading /dev/hdg[Input/output error]
ERROR: lsi: reading /dev/hdg[Input/output error]
ERROR: nvidia: reading /dev/hdg[Input/output error]
ERROR: pdc: reading /dev/hdg[Input/output error]
ERROR: pdc: reading /dev/hdg[Input/output error]
ERROR: pdc: reading /dev/hdg[Input/output error]
ERROR: pdc: reading /dev/hdg[Input/output error]
ERROR: pdc: reading /dev/hdg[Input/output error]
ERROR: sil: reading /dev/hdg[Input/output error]
ERROR: via: reading /dev/hdg[Input/output error]
/dev/hdf: pdc, "pdc_bgfdabigeg", stripe, ok, 120103040 sectors, data@ 0
/dev/hdh: pdc, "pdc_cdgjhjccf", stripe, ok, 78165248 sectors, data@ 0

Pleace Help!!!

Regards Phlip19

---

