---
title: "mount not working after upgrade"
date: 2008-09-05
forum: General Help
---

### Post by Dmole on 2008-09-05
objective : mount the same share to 2 folders with different permissions.

I used to use:

```
mount -t smbfs -o username=user,password=long-password,fmask=0555,dmask=0555,gid=1000 //ip/share /media/folder
```

now that smbfs, dmask, fmask, and long-password are deprecated or something I am using:

```
mount -t smbfs -o username=user,password=short-password,dir_mode=0555,file_mode=0555,gid=1000 //ip/share /media/folder
```

I have tried various combinations but I can't get mount to mount more then one time eg:
//ip/share to /media/folder
and
//ip/share to /media/otherFolder

I tried to use mount --bind to get around this but it ignores my masks/modes.


If anyone can shine some light on this I would be most grateful.


> cat /proc/version
Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008

---

### Post by Dmole on 2008-09-10
workaround:
so apparently the -r and -w options work but do not effect the displayed permissions
ls -al will say -rwxrwxrwx when in fact it could be -r--------

---

