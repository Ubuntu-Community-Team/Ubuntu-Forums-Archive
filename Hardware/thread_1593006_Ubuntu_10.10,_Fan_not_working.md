---
title: "Ubuntu 10.10, Fan not working"
date: 2010-10-11
forum: Hardware
---

### Post by andydch on 2010-10-11
Hi,

After install Maverick, my laptop fan is not spinning. How to solve that problem?
I'm using Toshiba Satellite L510 with Intel Core I3

Thanks

---

### Post by snafu006 on 2010-10-11
Have you tryed this [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780) that should help if not the old workaround still works hold FN(key)F3 the problem with toshiba laptops in that toshiba only likes windows. I have a toshiba L355-s7907 and my fan work.

---

### Post by andydch on 2010-10-11
after I add parameter **acpi_osi=Linux** and **acpi=copy_dsdt** into the grub, my fan work :D

---

### Post by snafu006 on 2010-10-11
Good the fan is running now you will see that the fan does not run very fast sometimes and its because toshiba only likes windows best thing to really do is get a fan pad to sit under the laptop there some good cheep ones out. anyways good to hear the fan is running laters

---

