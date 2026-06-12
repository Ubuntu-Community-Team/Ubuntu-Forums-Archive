---
title: "acpi sleep -- how to get it to stay sleeping?"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by edheil on 2005-09-12
Following guidelines here -- [https://wiki.ubuntu.com//HoaryPM](https://wiki.ubuntu.com//HoaryPM)  -- I enabled acpi sleep on my Acer Aspire 3002LCi.  When I execute 'sudo /etc/acpi/sleep.sh' it seems to shut down (the screen blanks and all that; I can see that it's releasing its dhcp lease, etc), but then it immediately perks back up again. 

Same thing if I hit the sleep button.

It seems as if everything about sleep works except staying sleeping.  Does that make sense?  Is there a fix?

Thanks

---

### Post by netsyd on 2005-09-13
You might try removing some of the modules that have been loaded... specifically anything for USB and WIFI. I recall that working on a system I had.

2 short scripts - 1 to remove the modules on sleep, 1 to insert them on resume.

---

