---
title: "Load Count On Laptop Drives"
date: 2009-01-04
forum: Hardware
---

### Post by eynestyne on 2009-01-04
Hello all, want to know if the load count issue that existed in version 8.04 has been fixed in version 8.10... I had 8.04 and my laptop but had to stop using it.

Thanks

---

### Post by cwbar_1 on 2009-01-04
Duplicate message.

---

### Post by cwbar_1 on 2009-01-04
Firstly, the hard drive cycle count was not exclusive to Ubuntu.  However, the problem seems to be fixed on 8.10.  See [https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)
If you want to check it for yourself, load smartmontools and run the following

smartctl -d ata -a /dev/sda  This is the command you would use for a SATA drive.

---

### Post by eynestyne on 2009-01-04
Thanks. :D

---

