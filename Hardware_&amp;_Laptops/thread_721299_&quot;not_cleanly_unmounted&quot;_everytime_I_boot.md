---
title: "&quot;not cleanly unmounted&quot; everytime I boot"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by shadowcaster00 on 2008-03-11
I mount my /home directory on a built-in SDHC card reader with a 8GB SDHC card inserted (/dev/sdb1, ext2),  Everytime when I boot the system(gutsy) it says that dev/sdb1 is not cleanly unmounted and force check.

If I boot in rescue mode, unmount /home, do fsck.ext2 /dev/sdb1, and then reboot,  it would be clean in the first reboot.  But if I reboot again( even with /home manually unmounted first), still it's not cleanly unmounted.

I have not a clue what's happening here.

---

