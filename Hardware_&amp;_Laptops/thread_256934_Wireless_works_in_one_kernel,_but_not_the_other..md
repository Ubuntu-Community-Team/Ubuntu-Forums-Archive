---
title: "Wireless works in one kernel, but not the other."
date: 2006-09-13
forum: Hardware &amp; Laptops
---

### Post by niko7865 on 2006-09-13
Clean install of Ubuntu. Installed linux-k7-smp, then followed [this](http://ubuntuforums.org/showthread.php?t=132980&highlight=rt61) guide while booted into the 386 kernel to make sure my wireless would work (Linksys WMP54G rt61).

Wireless works fine in 386 still, however when I do 'sudo dhclient ra0' while booted the the k7 kerenel it will display the first DHCPREQUEST and do nothing for several seconds, this is all it will ever display. After that my entire computer will momentairly freeze and when it comes back I loose keyboard support. The mouse still works fine but pressing any key will do nothing, other then that the system is fine although still not connected to the internet.

---

### Post by IcemanV9 on 2006-09-14
Do you have more than one CPU? If not, remove linux-k7-smp and install linux-k7 instead. Remember linux-k7 & linux-k7-smp are metapackage. One or two packages may be not installed correctly. You may want to re-install to make sure.

Also, you may want to try this solution --> [http://www.ubuntuforums.org/showthread.php?t=132980&highlight=Linksys+WMP54G+rt61](http://www.ubuntuforums.org/showthread.php?t=132980&highlight=Linksys+WMP54G+rt61)

If the problem (wireless) persists with linux-k7 or linux-k7-smp, then you may want to file a bug report. And, stay with linux-386 for a while. :/

---

