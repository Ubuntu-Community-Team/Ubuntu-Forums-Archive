---
title: "mounting of ntfs/ext3 partitions"
date: 2008-08-31
forum: General Help
---

### Post by _tom_ on 2008-08-31
Hello,

I have just a basic question (no problem with ubuntu at all).

In ubuntu I can see all my partition without an /etc/fstab entry on the desktop (in dolphin places). I can mount them very easy by clicking on them. With opensuse this doesn't work (no icons for the drives/partitions at all).

So how does Ubuntu mount ntfs/ext3 partition without needing an /etc/fstab entry? Is it a udev rule?

Tom

---

### Post by arkara on 2008-08-31
As far as i know ubuntu fully utilizes the fstab file.

---

### Post by raja on 2008-08-31
What the original poster means is that in Ubuntu, even partitions that dont have a fstab entry and are therefore not mounted while booting, will show up (unmounted) in the file manager. There is usually an option to mount in the right click menu and this mounts it under /media. 
I dont know about opensuse, but again, if you need this, it is easy to mount it manually when required.

---

### Post by arkara on 2008-08-31
Yes, now that you say so i can see my windows partition on kde but my windows partition does not have any fstab entry. when i try to mount it form cli i can't.
so i edit my fstab file and stil can't mount it from the cli.
the fstab line is.

 /dev/sda1       /media/sda1     ntfs-3g     defaults,utf8         0       0

and i get the following answer

mount /dev/sda1
mount: only root can mount /dev/sda1 on /media/sda1

why is that?

---

### Post by _tom_ on 2008-08-31
Thanks for your answers,

@arkara:
I think this should be
/dev/sda1 /media/sda1 ntfs-3g user,defaults,utf8 0 0

@raja:
Yes, you described it better then I did. The partitions without an fstab entry are not mounted but show up (and I like this behavior very much). So I want opensuse to behave the same and thus the question 'how is it done in ubuntu?'

---

### Post by arkara on 2008-08-31
i get this message with this configuration

```
aris@Kubuntu:/$ mount /dev/sda1
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged

```

but the wierd thing is..

```
aris@Kubuntu:/$ ls -l /bin/ntfs-3g
-rwxr-xr-x 1 root root 36972 2008-05-30 19:49 /bin/ntfs-3g

```

---

