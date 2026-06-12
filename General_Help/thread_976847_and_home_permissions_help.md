---
title: "/ and /home permissions help"
date: 2008-11-09
forum: General Help
---

### Post by Trzone on 2008-11-09
I used the live cd to backup both my / and /home partitions to 2 tars
unfortunately it backed up the directories /media/disk-1 and /media/disk within those two archives.

Then i used root (on live cd) to move the folders up to / and /home level
Meaning i changed the permissions
Does anyone know how to change the permissions back?
I haven't lost any data, it's just i don't have permissions to access the folders needing to boot up and such.
Any ideas? :)

Attached is my /etc/fstab

---

### Post by jpkotta on 2008-11-10
If you've lost the permissions, there isn't an easy way to restore them.  We can guess at what they should be though.

This sets all directories to be readable and listable by everyone, and also writable by root.
```
sudo find / -type d -exec chmod 755 '{}' ';'
```

Almost surely everything in these directories need to be executable by all.
```
sudo chmod 755 /bin/* /usr/bin/* /sbin/* /usr/sbin/* /usr/local/bin/*
```

But if you backed up with tar, the permissions should all be there.  Try extracting with the -p option, and do it as root.
```

[ubuntu@livecd]$ sudo tar xpf root.tar /media/rootmountpoint/
[ubuntu@livecd]$ sudo tar xpf home.tar /media/homemountpoint/

```

---

