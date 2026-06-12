---
title: "Unable to mount after re-format ???"
date: 2008-10-31
forum: Hardware
---

### Post by connord94 on 2008-10-31
So, I formatted a partition from NTFS to EXT3, and now it won't mount!

The partition is /dev/sdb1/, but it doesn't appear in /etc/fstab/ or /etc/mtab/.

When I double click it in 'Computer' I get "NTFC Signature is missing etc. etc. etc."

How can I get it working again? I was hoping to move my 'home' to it, so I can install Intrepid Ibex and keep my crap.


Thanks,




Connor


++++EDIT+++

fdisk -l says it's still 'HPFS/NTFS'  ???


Cheers,




Connor

---

### Post by connord94 on 2008-10-31
A simple restart did the trick, but fdisk still lists it as 'HPFS/NTFS', and not 'Linux' or 'Ext 3' of whatever.

Any ideas why?


Connor

---

