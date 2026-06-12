---
title: "1008HA - eth0 disappears after resume"
date: 2010-01-23
forum: Hardware
---

### Post by jlamanna on 2010-01-23
Hi,
I'm running network remix 9.10 with the atl1e (v 1.0.1.4) driver.
eth0 works great until I hibernate/suspend + resume. Then I can't get eth0 back until I restart. This is even the case if I remove the kernel module before suspend and reinsert it after resume.
I have to assume the ethernet chip isn't suspending properly so it doesn't come back up.

Has anyone else experienced this?

Thanks.

---

