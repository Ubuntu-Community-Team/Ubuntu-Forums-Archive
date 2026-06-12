---
title: "No read/write permissions on new hard drive"
date: 2008-04-18
forum: Hardware &amp; Laptops
---

### Post by ali999 on 2008-04-18
Hi, 

I recently installed a new hard drive on my computer and have edited all fstab file and everything so I can mount it just fine. My problem is however that I don't have full read/write permissions for this hard disk. I tried the following command that I found on another post:
sudo  chmod  -R  777  /<mount point>
However with this I only have permissions for the lost and found folder. I cannot create any other folders or anything. Can anyone help? Thanks.

---

### Post by Diabolis on 2008-04-18
try changing the owner of the folder(mount point). It is very similar to changing its permissions.
```
sudo chown *username*:*group* <mount point>
```

You are not forced to specify the group name, the user name should be enough.

---

### Post by ali999 on 2008-04-18
Worked like charm. Thanks.

---

### Post by ali999 on 2008-04-18
Worked like a charm. Thanks.

---

### Post by Diabolis on 2008-04-18
cool, don't forget to mark the thread as solved.

---

