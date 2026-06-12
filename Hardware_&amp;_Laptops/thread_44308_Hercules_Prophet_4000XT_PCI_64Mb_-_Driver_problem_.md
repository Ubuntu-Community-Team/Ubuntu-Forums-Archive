---
title: "Hercules Prophet 4000XT PCI 64Mb - Driver problem - modversions.h"
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by Psycho275 on 2005-06-25
Hello all,

I've been using Ubuntu for a while now, and recently found an old Hercules Prophet 4000XT PCI which I used to use a few years ago. I've decided to set up dual-monitors, but I can't get the Hercules Prophet to work.

Basically, I've edited xorg.conf to use dual monitors, but discovered my Hercules didn't work. I modified xorg.conf to use just the Hercules, but x failed on start up due to not finding the powervr drivers. After a little trying of installation / removal of the drivers, I discovered that it couldn't find moversions.h in /usr/src/linux/includes/linux. I've installed the kernel-source and linux-headers packages, but modversions.h isn't included in either of them.

Any help would be appreciated,
Dave

---

### Post by Psycho275 on 2005-06-26
Sorry to bump, but I really do need to get this working.

---

