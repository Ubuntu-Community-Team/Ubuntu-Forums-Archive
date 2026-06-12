---
title: "My CD drive doesnt detect ANYTHING"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by oomar on 2008-02-20
i need to reinstall the driver for my cd drive. It thinks it works but doesnt detect or write anything to discs... it doesnt even know they are there. how do i re install?

---

### Post by Yellow Pasque on 2008-02-20
Make sure that your drive is not being seen before trying to reinstall it. Does this command print a line for your CD drive?
```
sudo lshw -businfo -C disk
```

---

### Post by oomar on 2008-02-20
it DOES display my cd drive.
```
Bus info          Device      Class          Description
========================================================
scsi@0:0.0.0      /dev/sda    disk           55GB TOSHIBA MK6026GA
scsi@1:0.0.0      /dev/cdrom  disk           CDRW/DVD CDD5263

```

but im trying to burn a cd but when i put stuff in it tries to read it and nothing happens.

---

