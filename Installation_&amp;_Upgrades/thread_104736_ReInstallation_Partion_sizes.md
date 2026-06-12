---
title: "ReInstallation Partion sizes"
date: 2005-12-16
forum: Installation &amp; Upgrades
---

### Post by mfarquhar on 2005-12-16
i have a 20GB HD
windows has half

how do i divide 10GB among Ubuntu with separate partitions
ie.
/
/root
/boot
/home
/etc
/var
/temp
/swap

or am i better off with just two partitions
/
and
/swap

---

### Post by Sutekh on 2005-12-16
Probably 3 partitions would be best;
/, /swap, and /home.  That way all your documents and settings can remain intact if you want to re-install over /.

With only 10GB (in my opinion);
/ - 4GB (maybe less, I think the default install is around 2GB)
/swap - 1 to 2 times you RAM
/home - whatever is remaining

---

