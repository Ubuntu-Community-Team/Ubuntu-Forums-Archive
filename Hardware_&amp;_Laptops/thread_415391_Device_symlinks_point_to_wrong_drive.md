---
title: "Device symlinks point to wrong drive"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by berserker on 2007-04-20
Just upgraded to Feisty yesterday but this problem has been persisting for as long as I can remember.

I have two DVD burners:  The Sony DRU-800A is the master and the DRU-500A is the slave on the same IDE controller.  The 800A is /dev/scd0 and the 500A is /dev/scd1.

However, the symlinks /dev/dvd, /dev/dvdrw, /dev/cdrom and /dev/cdrw all point to /dev/scd1.

I can delete them and have the dvd symlinks point to scd0 and the cd symlinks point to scd1 but they all go back to pointing to scd1 after a reboot or even after I access the drives.

Any ideas how I can change this behavior?

Thanks.

---

### Post by berserker on 2007-04-21
Anyone have a similar problem?

---

### Post by Jergar on 2007-05-13
I have the same problem but no solution until yet.

Regards
Wolf

---

