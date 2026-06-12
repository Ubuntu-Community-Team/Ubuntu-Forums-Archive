---
title: "Nvidia problems with new kernel"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by DDRFreak21 on 2007-06-11
The problem I had was that after updating my kernel to the newest one my system would be unable to load x, stating that it was unable to load the nvidia kernel modules.

My solution i found was to reboot and use the old kernel startup entry to troubleshoot.
What i found out was that the restricted-drivers-manager for the new kernel version had not been installed along with the new kernel. So i installed the new restricted-drivers-manager-2.16.20-28 package, rebooted and had no problems :)

I guess i could have done that in the text mode that i got shot into after X failed but oh well ^.^

Just thought i'd put it out there if anyone else was having that problem.

---

