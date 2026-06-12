---
title: "root own my secondary hdd"
date: 2009-04-05
forum: Hardware
---

### Post by maclin on 2009-04-05
hi i need help! i just put in a old hdd that works fine but when i formated it it formated to work with ubuntu but now the root user owns and a cant do anything with it how do i give my self read and right privileges.

---

### Post by taurus on 2009-04-05
What filesystem did you format it to and where do you mount it--mount point?

```
sudo fdisk -l
cat /etc/fstab
df -h
id
```

---

### Post by ajgreeny on 2009-04-05
You may just need to edit the /etc/fstab file to make sure it is mounted properly, and also change the permissions of the drive/partition using chmod.  The output from the commands shown in the last post will help a lot.

---

