---
title: "let me pick your brain...scsi issue"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by makisupa123 on 2005-12-05
I have breezy on a sata drive which is sda.  When i install a scsi controller card and drive i select ubuntu in grub and it starts to boot except it fails shortly because the new scsi drive is assigned the 1 scsi drive position and the sata drive i presume ends up sda1.  Any clever ideas on how to get around this?

Thanks,

mak

---

### Post by PaganHippie on 2005-12-05
The first thing that comes to my mind would be to re-configure grub, telling it to load linux from sdb1 (not sda1, that would be the new SCSI drive, not the SATA).

---

### Post by metoo on 2005-12-05
Well, if the SATA drive is sda, then the partitions on it are numbered sda1, sda2 and so on. Another drive will be named sdb and would have the partitions sdb1, sdb2 and so on (if it has more than 1 (sdb1) partition).

So if your SCSI controller is now #1, you have to options.
1st
check your BIOS, if you have an option like boot internal first.
2nd
when in grub, hit e, select the line with kernel and try replacing the sda entry with sdb. This is not permanent, but lets you try if this solves your problem. If it does, do the re-install of grub. You can come away with altering /boot/grub/menu-lst, but only until the next kernel update from ubuntu. So re-configuring grub is the better solution.
The irritating thing is, that your grub is installed and boots on hd0. So your system still sees your SATA hd as the first one?

---

