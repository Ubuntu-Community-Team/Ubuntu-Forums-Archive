---
title: "[SOLVED] setfacl not working"
date: 2008-08-29
forum: General Help
---

### Post by cgkades on 2008-08-29
```

hostname$ sudo setfacl -m u:test:w tmp
setfacl: tmp: Operation not supported

```

rw or x in place of w does the same thing
tmp is a directory, and test is a user i created

using ubuntu 8.04

what am i doing wrong?

---

### Post by jigsaws on 2008-08-29
Hello

First - check which filesystem is /tmp :
mount
is it in / or /tmp filesystem

The remount filesystem with acl parameter:
sudo mount -o remount,acl /tmp

You can also add acl to default mount parameters at /etc/fstab

---

### Post by cgkades on 2008-08-29
> **jigsaws said:**
> Hello

First - check which filesystem is /tmp :
mount
is it in / or /tmp filesystem

The remount filesystem with acl parameter:
sudo mount -o remount,acl /tmp

You can also add acl to default mount parameters at /etc/fstab

ohhhh, you have to mount the filesystem witht the option acl to tell it your using acls? its not automatic i take it? tmp is in /home/tmp

---

### Post by cgkades on 2008-08-29
got it all working, thank you!

---

### Post by jigsaws on 2008-08-29
No, acl must be specified in mount parameters or in default filestestem's mount parameters which you can set by tune2fs -o.

---

