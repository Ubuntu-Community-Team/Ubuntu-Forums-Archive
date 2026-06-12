---
title: "DVD burners not working properlly"
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by drx0 on 2006-11-13
Mounting CDs and DVDs in either of my two DVDRW drives is a very hit and miss thing (mostly they don't mount and the error reported is usually "No medium found". I can't burn anything at all.  Gnomebaker says it's copying but kicks out the CD and crashes and CD/DVD creator just says "there was an error."  They are working in Windows on the same PC -- NOT a configuration problem.  It fails with the GUI mounter and with the sudo mount...

Any ideas? Thanks much in advance!

Btw, my fstab file is as follows:

admin@admin-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
UUID=6db68e34-858b-46fe-89fb-2de0ea2e0db3 / ext3 defaults,errors=remount-ro 0 1
# /dev/sdb5
UUID=f534c70c-133d-40ac-bdbd-bdd020f13010 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0

---

### Post by jamesr on 2006-11-13
What version of Ubuntu, because I am having difficulties with Edgy of similar nature , not DVDs only CDRs. I was wondered if the problem was associated with the change 0f the core of linux and the change that scsi emulation is no longer needed. With some people it seeems to have had a positive effect in that the burning speed has done from >1X to 16X. But others not so positive.

---

