---
title: "mount a folder"
date: 2008-10-16
forum: General Help
---

### Post by marshal on 2008-10-16
hi,

is it possible to mount a folder to another folder?

i want to have one partition with the folder /var/www and /var/mysql

i mounted this partition to /test
mount -t ext3 /dev/sdb1 /test

on this partition i have created 2 folders, www and mysql
now i tried
mount /test/www /var/www

but it is not allowed =)

i hope someone can understand what i mean and help me =)

---

### Post by hyper_ch on 2008-10-16
did you try symlinks?

---

### Post by sisco311 on 2008-10-16
```
mount -o bind /test/www /var/www
```

---

### Post by marshal on 2008-10-16
ahh, great it works.

... is it possible to add this to fstab?

---

### Post by sisco311 on 2008-10-16
> **marshal said:**
> ahh, great it works.

... is it possible to add this to fstab?

yes:
> /test/www /var/www auto bind

---

