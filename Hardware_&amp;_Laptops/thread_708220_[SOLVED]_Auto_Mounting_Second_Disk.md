---
title: "[SOLVED] Auto Mounting Second Disk"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by Xander {MP} on 2008-02-26
Well I have finally done it I have switched over to Linux!!! I am running a dual boot system, but now instead of running to windows I now run to Linux. Anyway I have three hard drives. Their is a master running Linux and a slave for extra storage dedicated solely to Ubuntu, and the third running windows. How do I get the slave to auto mount at start-up?


Thanks,

Xander {MP}

---

### Post by jan quark on 2008-02-27
you have to edit your fstab file

first please post the output of these terminal commands:


```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

