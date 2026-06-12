---
title: "How to know which drive for what logical name?"
date: 2009-08-02
forum: Hardware
---

### Post by meka4996 on 2009-08-02
How to know which cd/dvd drive/rom/rw is for what logical name like /dev/cdrom or /dev/cdrom1 or /dev/dvd0 ???

Is there an optical drives device mapping report?

---

### Post by meka4996 on 2009-08-02
Yes, there is: $ sudo lshw -C disk

---

