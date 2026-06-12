---
title: "specifiying the mounting folder for a hard drive disc ?"
date: 2010-12-05
forum: Hardware
---

### Post by Zib.c on 2010-12-05
Hello everybody,
I have a little problem concerning a hard drive ...

In fact, it's an external hard drive but i use a "rack" to plug it in a internal sata plug (via e-sata plus on the hard drive). however I also use it with a usb plug from time to time

currently i use this configuration in fstab but, i'm not allowed to unmount it (as a simple user)
```
# mount WORK
UUID=3CB6D26AB6D22464    /home/zib/Work    ntfs    defaults    0    0

```so how could i do to specify the mounting folder and being able to unmount it without using "sudo" ??

thanks!

ps : if anything is unclear please tell me!

---

### Post by sikander3786 on 2010-12-05
Adding umask, uid and gid might help.

Your mount definition will look like this in /etc/fstab.

```
UUID=3CB6D26AB6D22464    /home/zib/Work    ntfs-3g    defaults,utf8,umask=007,uid=1000,gid=1000 0 **1**
```

---

