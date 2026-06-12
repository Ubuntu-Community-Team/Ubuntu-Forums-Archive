---
title: "help me uninstall"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by ruialexbarbosa on 2007-01-09
Hi, when I try to uninstall my modem I get this error, how can I do it?

alex@vaio:~$ sudo dpkg --force-all -r conexant
Password:
(Reading database ... 90702 files and directories currently installed.)
Removing conexant ...
ERROR: Module hsfserial does not exist in /proc/modules
ERROR: Module hsfengine does not exist in /proc/modules
ERROR: Module hsfbasic2 does not exist in /proc/modules
ERROR: Module hsfosspec does not exist in /proc/modules
dpkg: error processing conexant (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 conexant
alex@vaio:~$

---

### Post by ruialexbarbosa on 2007-01-09
done!

---

### Post by ruialexbarbosa on 2007-02-05
Here's how I did it:

sudo rm /var/lib/dpkg/info/conexant.postrm
sudo dpkg --force-all -r conexant

---

