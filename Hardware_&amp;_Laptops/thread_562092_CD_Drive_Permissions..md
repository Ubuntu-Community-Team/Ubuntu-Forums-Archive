---
title: "CD Drive Permissions."
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by Alucard-sama on 2007-09-28
Everytime I try to mount my CD drive I get this message:
You do not have the permissions necessary to view the contents of "cdrom0".

How do I get the necessary permissions?

---

### Post by eggdeng on 2007-09-28
You need to prefix sudo to the mount command.

---

### Post by Alucard-sama on 2007-09-28
K.
It mounts now, but I still get the same message when I try to view the files on it.

---

### Post by eggdeng on 2007-09-29
Assuming the CD is mounted at /media/cdrom0, do
```
sudo ls -l /media/cdrom0
```
If you can see the files, then it is a permissions problem. Check that your user has the appropriate privileges: System->Administration->Users & Groups->highlight your user and click Properties. On the User Privileges tab, check that all the boxes are ticked.

---

### Post by Linicks on 2007-09-29
Ignore...

---

