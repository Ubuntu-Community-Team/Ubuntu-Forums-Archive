---
title: "Compaq Presario R3000 kernel panic"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by ton.boelens on 2005-10-16
Hi,

After installing Ubuntu Breezy Badger AMD64 for the first time, the system tries to boot and then I get the following error messages:

kmod: failed to exec /sbin/modprobe -s -k scsi_hostadapter, errno = 2
kmod: failed to exec /sbin/modprobe -s -k scsi_hostadapter, errno = 2
kmod: failed to exec /sbin/modprobe -s -k scsi_hostadapter, errno = 2
Kernel panic: VFS: Unable to mount root fs on 03:07

My guess is that Ubuntu thinks that my laptop is SCSI-based, but it is an IDE system.

Does anybody have an idea?

Thanks,

Ton

---

### Post by ton.boelens on 2005-10-16
The problem does not occur if I choose another menu-option from the GRUB-list, so now I can continue with finallising the install.

Ton

---

