---
title: "Migrate ubuntu from 1 partition to another"
date: 2006-03-03
forum: Hardware &amp; Laptops
---

### Post by A-star on 2006-03-03
Hi all,

I want to migrate my installation from one partition to another.
currently it is on hdb1 and I want to move it to hdb3.

How can this be done without reinstalling everyting?

any help or tips on how to do it?

---

### Post by Xian on 2006-03-03
1. Create the new partition (use gparted or similar).
2. Use [Rsync](http://www.ss64.com/bash/rsync.html) to transfer the data.
3. Change your /etc/fstab to reflect the new mount points.
4. Reconfig (and install again if needed) grub.
5. Wipe the old partition.

---

### Post by Orpheus- on 2006-03-04
Or alternatively, boot from a live CD and cp -a everything. I personally prefer not to copy a root partition while it's in use.

---

