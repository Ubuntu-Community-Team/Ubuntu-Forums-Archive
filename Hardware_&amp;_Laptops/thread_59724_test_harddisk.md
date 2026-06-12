---
title: "test harddisk"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by shizow on 2005-08-25
how can i test my harddisk

i have a new ibm t43 and my laptop freezes out very sporadically
i tested the ram with memtest, that was ok

so i want to test my harddisk, how can i do this?

---

### Post by heimo on 2005-08-25
Bonnie (package: bonnie++) is probably meant for performance testing, but it could be useful for you too:
[http://packages.ubuntu.com/hoary/utils/bonnie++]("http://packages.ubuntu.com/hoary/utils/bonnie++")


Oh, and if you don't yet know about hdparm, that's one great utility to check your drives' settings.

---

### Post by luca_linux on 2005-08-25
Also:
```
sudo hdparm -Tt /dev/hda
```
Note: "hda" is the hd you want to test.

---

