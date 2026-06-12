---
title: "Target file system doesn't have /sbin/init"
date: 2014-11-25
forum: Hardware
---

### Post by shurguywutt on 2014-11-25
I have Ubuntu 14.04 x64 installed on my Dell e6410 laptop.  Everything is working fine.  The battery died the other day and the next boot cycle had this to say on next boot.

```
mount: mounting /dev/disk/by-uuid/***************************** on /root
failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

```

I was able to recover using live cd and this blog page.
[http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html]("http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html")

Is there any way I can prevent this from happening in the future with a power failure as laptops do run on batteries and eventually all batteries die?

Thanks in advance!

---

### Post by shurguywutt on 2014-11-26
Seems how I need to do the following with the Live CD,

> sudo fsck /dev/sda1

 a fix may be to modify the init file to mount the drive as sda1 instead of using a unique ID.

I would be interested to know what others have to say about this issue as it is probably pretty common with laptops running ubuntu.

---

