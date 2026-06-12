---
title: "How do I find out if a specific driver is already included in the kernel?"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by xp_newbie on 2006-11-04
How do I find out if a specific driver is already included in the current Ubuntu 6.0.6 kernel (2.6.15-27.48)?

Or if its missing?


Thanks!
Alex

---

### Post by 23meg on 2006-11-04
If you know the module name you can do ```
lsmod | grep module_name
```to see if that module is loaded.

---

### Post by Sef on 2006-11-04
Or you could post the driver you are wondering about in the forums.

---

### Post by dbott67 on 2006-11-04
Check here:

[http://www.linuxhq.com/kernel/v2.6/15/drivers/index.html](http://www.linuxhq.com/kernel/v2.6/15/drivers/index.html)

-Dave

---

### Post by schorsch on 2006-11-05
Just type:

grep "wanted_driver_name" /lib/modules/`uname -r`/modules.dep

this will reveal, if the driver is included in the current kernel.

---

### Post by xp_newbie on 2006-11-05
OK, thanks everybody!

So, I did:

[FONT="Courier New"]> ~> lsmod | grep promise
sata_promise           12516  8 
libata                 83440  1 sata_promise
scsi_mod              145960  6 sr_mod,sbp2,sg,sd_mod,sata_promise,libata
[/FONT]
And:

> ~> grep promise /lib/modules/`uname -r`/modules.dep
/lib/modules/2.6.15-27-686/kernel/drivers/scsi/sata_promise.ko: /lib/modules/2.6.15-27-686/kernel/drivers/scsi/libata.ko /lib/modules/2.6.15-27-686/kernel/drivers/scsi/scsi_mod.ko


Which seems to suggest that the driver for the Promise FastTrack 387 *is* loaded. But a different piece of information elsehwere, the [Debian kernel-patch-2.4-fasttraks150]("http://packages.debian.org/stable/devel/kernel-patch-2.4-fasttraks150"), states:

[B]> WARNING: There will be no support for Linux 2.6 kernels!

[/B]
How do you reconcile between what my system reports and the seemingly contradicting statement on the Debian kernel page?

Thanks!
Alex

---

