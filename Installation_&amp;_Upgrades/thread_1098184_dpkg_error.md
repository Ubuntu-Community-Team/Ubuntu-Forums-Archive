---
title: "dpkg error"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by wisd0m on 2009-03-16
When running updates or trying to install new programs, I get:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

When I try to run *dpkg --configure -a* I get this message:

```
wisd0m@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for wisd0m: 
dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 field name `/usr/share/menu' must be followed by colon
luke@ubuntu:~$ 
```


Any help would be great.

---

### Post by PenguinsFan on 2009-03-16
I'd try to delete the file mentioned in the error and rerun

```

sudo rm /var/lib/dpkg/updates/0000;sudo rm /var/lib/dpkg/updates/0001;dpkg --configure -a
```

There are a few other threads on this topic too if you need more ideas!

---

### Post by wisd0m on 2009-03-16
thanks for the help, i get this now.

```
wisd0m@ubuntu:~$ sudo rm /var/lib/dpkg/updates/0000
[sudo] password for wisd0m: 
wisd0m@ubuntu:~$ sudo rm /var/lib/dpkg/updates/0001
wisd0m@ubuntu:~$ sudo dpkg --configure -a
dpkg: unable to stat triggers deferred file `/var/lib/dpkg/triggers/Unincorp': Stale NFS file handle
wisd0m@ubuntu:~$ 
```

I installed this machine via Wubi, its on top of vista.

---

### Post by PenguinsFan on 2009-03-16
Hmmm - Well, lets refresh the NFS file handle.

Have you tried a good ole' fashion reboot? :D

---

### Post by wisd0m on 2009-03-16
> **PenguinsFan said:**
> Hmmm - Well, lets refresh the NFS file handle.

Have you tried a good ole' fashion reboot? :D


Yes, I rebooted first.

---

### Post by wisd0m on 2009-03-16
ok, i rebooted and did fsck. it works now. i had half-installed supertux2 and i think it was causing the issue.

thanks for your help

---

