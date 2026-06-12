---
title: "Issues external HDD encrypted"
date: 2010-09-29
forum: Hardware
---

### Post by kate9954 on 2010-09-29
Please help, guys, if you can.  I think this post is in the right place, as it has to do with a HDD partition, but if it needs moving, feel free.  I am using Ubuntu 10.04 Lucid with Gnome desktop, most current everything.

I have a partition on a very large external HDD encrypted with Truecrypt - device (entire partition) encrypted, not file container.  Drive was 1TB.  I had a 178GB unencrypted backup partition, and the rest was the encrypted drive.  I needed to reduce the size of the unencrypted partition and did, leaving 22GB unallocated.  This was using GParted, and it appeared to work without damaging the large encrypted partition.

After rebooting, the large partition has gone missing.  Truecrypt can't see it, and neither can Ubuntu (GParted).  It shows as unallocated space.  I am running Testdisk right now to try to find it, but I am afraid it will not be found because of the encryption (Truecrypt formatted to ext3, but without Truecrypt, it should appear random).  I have most carefully NOT written to the drive since this happened.

I am fairly tech savvy, but in software, not hardware.  Manually repairing a partition table makes my head spin.  Is there any way to recover the data I have lost?  

Thanks for your time,

Kate

---

