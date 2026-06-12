---
title: "Problem with wireless connection after upgrade"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by chkhurum on 2009-09-29
I upgraded from 8.04 to 9.04 but found out that the system is not stable. The new ubuntu does not had support for graphic drivers, sound drivers, wireless connection, mobile internet serivice. 

Some one suggested that i moved to new kernel 2.6.30 and that solved the problem of graphic drivers. But wireless network seems totally dead. It was working out of the box in 8.04 but dont know why Ubuntu does not support it anymore. by using lspci i found out that following is my card name
Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection

I tried to find out following site for getting the drivers but process fails when i try to "make". it says "Kernel Makefile not found at '/lib/modules/2.6.30-020630-generic/source"

Does anyone knows how to solve wireless problem? Urgent help will be appreciated.

---

### Post by chkhurum on 2009-09-29
That was the site i tried to install the drivers but failed.
[http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi)

---

### Post by chkhurum on 2009-09-29
By doing following gives no errors.
$ modprobe mac80211
$ modprobe iwl4965

---

### Post by chkhurum on 2009-09-30
Any help please. 
Or it is a known issue that wireless support is not available on latest versions of Ubuntu.

---

