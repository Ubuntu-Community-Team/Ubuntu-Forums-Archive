---
title: "Boot fails with PCI video card"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by navilon on 2006-12-20
Hello,
I'm running Ubuntu 6.10 just fine until I insert the Nvidia Geforce2 MX400 PCI card. When I boot up the machine I get a kernel panic. I have an onboard Intel AGP video card which cannot be disabled. I would show you the exact error message i received at boot, but i do not know where to retrieve this log file.
Any help would be greatly appreciated.

Thanks,
Simon

---

### Post by po0f on 2006-12-20
navilon,

Try passing "agp=off" as a kernel parameter when you boot.  Also, [this](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated) should help.

---

