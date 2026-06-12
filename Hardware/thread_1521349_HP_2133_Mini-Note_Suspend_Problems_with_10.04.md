---
title: "HP 2133 Mini-Note Suspend Problems with 10.04"
date: 2010-06-30
forum: Hardware
---

### Post by awg on 2010-06-30
Hi Everyone,

I have an HP 2133 Mini-Note, which has had Ubuntu on it basically since I bought it.  Sometime after upgrading to 10.04 from 9.04, it decided it would no longer suspend to RAM, which worked fine before.  I've done a clean install of 10.04 (server install then apt-get install xubuntu-desktop), but it still doesn't work.

cat /proc/acpi/sleep says S0 S4 S5, indicating that the kernel doesn't think suspend (S3) is supported.

Has anyone had this issue with 10.04 and solved it?  Or is it an upstream kernel bug?

Thanks.

---

