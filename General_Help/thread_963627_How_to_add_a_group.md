---
title: "How to add a group?"
date: 2008-10-30
forum: General Help
---

### Post by d0nut on 2008-10-30
I don't know how to add a new group from the command line.  Can anyone assist me?  Thanks.

---

### Post by x1a4 on 2008-10-30
Hi,
/usr/sbin/groupadd is used to add a group.
```
/usr/sbin/groupadd -g 1856
```
will create a group with group ID (GID) 1856

---

### Post by Titan8990 on 2008-10-30
/usr/sbin is in the default $PATH variable so there should be no reason to define the absolute path. In Debian based distros addgroup and adduser should be used instead off groupadd and useradd. Also, you will need to sudo it:


sudo addgroup

---

### Post by d0nut on 2008-10-30
Titan8990,

Thanks for that info.  My textbook, relating in general to UNIX-type systems, said to use groupadd and useradd.  Thanks for clearing up that it is different for Debian based systems.

---

