---
title: "sever trouble"
date: 2009-01-09
forum: Hardware
---

### Post by microchoc on 2009-01-09
i have installed ubuntu server 8.10 on my serveer and it says 

attemping to boot from hard drive C:


what should i do

---

### Post by linux_tech on 2009-01-09
what is output of ```
sudo fdisk -l
```

Do you have any other OS installed on the computer?

Is it sata, ide, or scsi?

---

### Post by igknighted on 2009-01-10
> **microchoc said:**
> i have installed ubuntu server 8.10 on my serveer and it says 

attemping to boot from hard drive C:


what should i do

If it says anything about c:, it is a windows issue, as windows is trying to boot.  There is no such thing as c: in linux.

---

