---
title: "Sata Hard Drives &amp; Boots"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by GaibryelRemorse on 2005-04-12
I couldn't find this anywhere else on the forums so... heres to posting...

if your having trouble getting a Sata device (mine is /dev/sda1 @ 300G ext3), and after LVM & EVMS (Large Volume Management & Enterprise Volume Management System) are throwing you to Root Console and not able to find said device... do this:

sudo /etc/modules
at the end add "sata_sil" and on the next line "scsi_mod"

works fine through a reboot over here and mounts where it should

---

