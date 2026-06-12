---
title: "SATA Support?"
date: 2006-08-06
forum: Hardware &amp; Laptops
---

### Post by pigeonor on 2006-08-06
I was wondering if anyone knew when Ubutnu would have SATA support?  All of my hard drives are SATA and when i try to install from Live CD, the install freezes up.

Please Help Out....

justin
[www.mmypaloma.com](www.mmypaloma.com)

---

### Post by Phasmagon on 2006-08-06
Ubuntu has SATA support. Maybe your chipset is not supported though unlikely.

---

### Post by pigeonor on 2006-08-06
i dont think it is my chipset, i have an asus a8n sli premium motherboard, with an athlon 3800 64 bit processor.  so what should be the problem now?

---

### Post by Nachtengel on 2006-08-13
Make sure that the installer is partitioning your disks correctly.  I know that has been a stubling block of mine on the same hardware.  I suggest having a dedicated /boot partition as well as your general /  root and swap.  Make sure that the /boot partition goes on sda, or it seems to not work.

---

