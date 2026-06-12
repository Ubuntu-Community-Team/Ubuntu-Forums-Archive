---
title: "[SOLVED] formatting"
date: 2008-10-07
forum: General Help
---

### Post by suhaib1thariq on 2008-10-07
how can i format a pen drive..a memor y card or even  a hard drive in hardy

---

### Post by iaculallad on 2008-10-07
> **suhaib1thariq said:**
> how can i format a pen drive..a memor y card or even  a hard drive in hardy

You can use the GParted utility to format drives. Or using the terminal:

```
sudo mkfs.ext3 /dev/sda1
```

---

### Post by suhaib1thariq on 2008-10-08
where can i find the gparted

---

### Post by jerome1232 on 2008-10-08
It's not installed by default, to install it
```
sudo apt-get install gparted
```

for added functionality
```
sudo apt-get install mtools ntfsprogs e2fsprogs jfsutils reiserfsprogs xfsprogs
```

---

### Post by suhaib1thariq on 2008-10-08
i installed it ....where can i find it...where it has been installed

---

### Post by jerome1232 on 2008-10-08
System->Administration->Partition Editor

---

### Post by bluemm on 2008-11-08
thanks for helping in this thread, it was helpful to me as well.

---

