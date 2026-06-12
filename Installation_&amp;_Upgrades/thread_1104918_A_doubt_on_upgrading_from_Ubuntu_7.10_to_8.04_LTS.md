---
title: "A doubt on upgrading from Ubuntu 7.10 to 8.04 LTS"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by ToniVC on 2009-03-24
Hi,

I need to upgrade my Ubuntu 7.10 server to 8.04 LTS version. I read on [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades) the following:

> Upgrade from 7.10 to 8.04 LTS

Known Problems

   1.

      The upgrade will freeze on the locales package if you are using the (current) Gutsy kernel, 2.6.22-**15**. Reboot into 2.6.22-**14** before upgrading. See the bug report on Launchpad for full details. 

Since I have kernel version 2.6.22-**16**-server installed, my question is: do I still have to reboot into 2.6.22-14, or my version has already corrected the locales package freeze bug?

Thanks,

Toni

---

### Post by albandy on 2009-03-24
I've been reading the kernel bugs page and tells that is a locale problem with kernel, after going to 2.6.22-16 bug page don't appear any bug refering to that, but if I were you I'll do it with 2.6.22-14

---

### Post by ToniVC on 2009-04-15
I finally did it with 2.6.22-16 kernel without any problem. Thanks.

---

