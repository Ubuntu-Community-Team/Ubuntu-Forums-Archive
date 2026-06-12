---
title: "[Printer]Canon MP276 cannot work...Help..."
date: 2010-08-26
forum: Hardware
---

### Post by Mr.Comix on 2010-08-26
I got a Canon MP276 All-in-one printer
and my system is Ubuntu 10.10 Alpha3 64bit
I cannot find a right driver for my Canon printer in programs offered by Ubuntu
neither,
I there's no driver for 64bit Linux on Canon's official site
how can I solve this problem
any idea?
thank you in advance
:KS

---

### Post by Malin@tor on 2011-03-07
> **Mr.Comix said:**
> I got a Canon MP276 All-in-one printer
and my system is Ubuntu 10.10 Alpha3 64bit
I cannot find a right driver for my Canon printer in programs offered by Ubuntu
neither,
I there's no driver for 64bit Linux on Canon's official site
how can I solve this problem
any idea?
thank you in advance
:KS

I've used "--force-architecture" option to install the x32 driver (MP270).
It works pretty fine

sudo dpkg -iG --force-architecture ./packages/cnijfilter-common_3.20-1_i386.deb
sudo dpkg -iG --force-architecture ./packages/cnijfilter-mp270series_3.20-1_i386.deb

---

