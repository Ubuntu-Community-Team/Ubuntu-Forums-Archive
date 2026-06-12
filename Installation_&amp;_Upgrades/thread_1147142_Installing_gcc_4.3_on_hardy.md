---
title: "Installing gcc 4.3 on hardy"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by anilcr on 2009-05-03
Hi guys can anybody tell me how I can install gcc 4.3 on hardy?

thanks
Anil

---

### Post by adit on 2009-05-07
That is impossible
gcc 4.3 depends on libc6(2.8), but the version installed on ubuntu hardy is libc6(2.7)
You can not update libc6 from 2.7 to 2.8 in ubuntu hardy, because several programs depend on libc6(2.7).  If you update to libc6(2.8), the entire system will break.  The only solution is to upgrade ubuntu hardy to ubuntu intrepid.

---

