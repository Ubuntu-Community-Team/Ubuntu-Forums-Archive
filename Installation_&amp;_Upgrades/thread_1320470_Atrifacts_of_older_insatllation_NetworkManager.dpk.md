---
title: "Atrifacts of older insatllation: NetworkManager.dpkg-backup"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by ravi.xolve on 2009-11-09
I upgraded Kubuntu from 9.04 to 9.10 and now I have a service as NetworkManager.dpkg-backup in /etc/init.d/

Why is it there? And any remedy for it? Please help.

---

### Post by lensman3 on 2009-11-09
"rm -f NetworkManager.dpkg-backup" using sudo.

You evidently modified the original NetworkManger file which didn't match the rpm (or equivalent).  So the installer kept the original.

---

### Post by ravi.xolve on 2009-11-14
thanks!

---

