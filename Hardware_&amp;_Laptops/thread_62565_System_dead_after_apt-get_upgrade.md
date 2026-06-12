---
title: "System dead after apt-get upgrade"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by kennywest on 2005-09-05
Hi all,

This saturday I did an apt-get update, apt-get upgrade and apparently the default kernel (i.e. the older 2.6.10) was updated. After restarting the system, the kernel could not find my SATA drive anymore. I have an Intel ICH6 SATA controller and it was working perfectly before the upgrade. The 2.6.11, also available in Ubuntu repository, is also not working for me. So I decided to compile my own kernel (2.6.13) and now everything is working fine. I even got sound working (Intel HD Audio, supported as of 2.6.12).
So I don't have a real problem, but I figure that not-so-experienced-users or people don't want to compile a kernel, can possible have problems.

---

