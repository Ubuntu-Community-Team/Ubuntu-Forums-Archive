---
title: "Installed 5.10 different from LiveCD?"
date: 2005-11-23
forum: Hardware &amp; Laptops
---

### Post by moregrey on 2005-11-23
Hi folks--
I recently tried out the 5.10 LiveCD and liked how it performed on my old Toshiba laptop (Satellite 2705). I went through the full installation process, and things are a little different now. In particular, the fan runs continuously. If I boot the LiveCD, the fan turns on and off as expected. When I boot back into the installed system, the fan always runs.
Anyone have ideas about this? Is there some permissions issue somewhere, or some hardware didn't get detected properly during the installation?
Thanks!

---

### Post by 23meg on 2005-11-23
Hi and welcome. Please paste the output of the following command:
```
lsmod |grep toshiba
```

---

### Post by moregrey on 2005-11-23
Hi, thanks for the reply. Here's the output:

$ lsmod |grep toshiba
toshiba_acpi           10940  0
$

I hope this means something!

---

