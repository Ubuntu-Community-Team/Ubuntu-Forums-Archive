---
title: "fsck"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by boersmaa on 2007-01-04
Hi,

I am getting the following error on booting edgy.

Log of fsck -C -R -A -a 
Thu Jan  4 18:24:45 2007

fsck 1.39 (29-May-2006)
/dev/hda1: clean, 31/52208 files, 19711/104391 blocks
fsck.ext3: Unable to resolve 'UUID=0864b96e-8705-4bb5-8bb9-04338fb891e1'

fsck died with exit status 8

Thu Jan  4 18:24:45 2007
----------------

I am not able to fix it with fsck, but I can boot into Edgy.

Anybody can give me any help on fixing it?

I have done all hardware tests and it gives me no hardware errors.

Thanks Andy

---

### Post by pay on 2007-01-04
You can't run it when the drive is mounted (well your not supposed to). Try running fsck from a liveCD or something.

---

