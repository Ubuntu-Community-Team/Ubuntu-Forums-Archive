---
title: "installing new hdd"
date: 2010-10-05
forum: Hardware
---

### Post by stuarttanner on 2010-10-05
hi all, i have just installed a second hard drive in my computer for backing up information, the problem is i can access the hard-drive but cant change files or add file to the drive as it says i am not root.
how can i change the permissions on this drive.

stu

---

### Post by viralmeme on 2010-10-05
> **stuarttanner said:**
> the problem is i can access the hard-drive but cant change files or add file to the drive as it says i am not root

Make sure non-root-user is a member of the users group. Then you need to find out where the harddrive is mounted. At a console and without the $ sign, type:

$sudo -i
$mount
$chown -R root:users /path/to/harddrive
$chmod -R g+rwx /path/tp/harddrive

---

### Post by stuarttanner on 2010-10-06
thank you all sorted now.

stu

---

