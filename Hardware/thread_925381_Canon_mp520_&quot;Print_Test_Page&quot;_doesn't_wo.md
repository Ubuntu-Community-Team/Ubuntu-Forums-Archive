---
title: "Canon mp520 &quot;Print Test Page&quot; doesn't work"
date: 2008-09-20
forum: Hardware
---

### Post by noban on 2008-09-20
Hi!

Using ubuntu 8.04 upgraded from 7.10. Installed first time mp520 on ubuntu 8.04 using default system drivers (probably it was mp500 drivers), printing worked but no scanning. After that downloaded original drivers from canon site (cnijfilter-common_2.80-1_i386.deb, cnijfilter-mp520series_2.80-1_i386.deb, scangearmp-common_1.10-1_i386.deb and scangearmp-mp520series_1.10-1_i386.deb)
Removed printer from printers list, installed, now scanning works fine, but not printing. 

I've tried to install turbo-driver no result - removed it, XWtools - same result. Printer is located by system once I'm deleting it from system and reisntalling base drivers (cnjfilter-common..., cnjfilter-mp520...), but printing test page does nothing - job 'is processing' and nothing is happening.

Any ideas - where to dig for solution?

---

### Post by noban on 2008-11-02
It was problem with permissions, after installation of scanner permissions on /dev/usb/lp0 changed. See [http://ubuntuforums.org/showthread.php?t=917631](http://ubuntuforums.org/showthread.php?t=917631) eventually sudo chown root.lp /dev/usb/lp0
worked fine :)

---

