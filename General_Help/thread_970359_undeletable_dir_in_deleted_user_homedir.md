---
title: "undeletable dir in deleted user homedir"
date: 2008-11-04
forum: General Help
---

### Post by jodgi on 2008-11-04
On an 8.04 LTSP system I have deleted a user with the GUI and wanted to delete the entire user homedirectory. I cannot delete a certain directory: .gvfs. I've tried sudo, su and logging in as root. 

```
admin@Hoth:/home$ sudo rm -rf user/
[sudo] password for admin: 
rm: cannot remove `user/.gvfs': Permission denied
admin@Hoth:/home$ sudo ls -la /home/user
ls: cannot access /home/user/.gvfs: Permission denied
total 8
drwxr-xr-x   3 admin 1099 4096 2008-11-04 10:44 .
drwxr-xr-x 153 root    root 4096 2008-11-04 10:40 ..
d?????????   ? ?       ?       ?                ? .gvfs
```

any ideas?

---

### Post by tonybaqain on 2008-11-04
use the following command instead:
```
 sudo userdel -r user
``` 
but make sure you are using another account session/login.

---

### Post by jodgi on 2008-11-04
Problem is I've already deleted the user in the GUI, so the userdel command only complains that the user doesn't exist.

how can a file/dir be inaccessible to root, sudo and su?

---

### Post by tonybaqain on 2008-11-04
make it funnier, do the following 
```

sudo useradd user
sudo userdel -r user

``` 

have fun :)

---

### Post by geirha on 2008-11-04
Try ```
sudo umount /home/user/.gvfs
```

---

### Post by jodgi on 2008-11-04
> **geirha said:**
> Try ```
sudo umount /home/user/.gvfs
```

Sorry (sort of) guys, in the mean time I've booted the box with RIPlinux and deleted the user homedir the hard way, successfully.

I tried to reproduce by adding and deleting a user and it went as expected and successfully. I noticed that the .gvfs had "normal" own and mods, and not as the troublesome:
```
admin@Hoth:/home$ sudo ls -la /home/user
ls: cannot access /home/user/.gvfs: Permission denied
total 8
drwxr-xr-x   3 admin 1099 4096 2008-11-04 10:44 .
drwxr-xr-x 153 root    root 4096 2008-11-04 10:40 ..
d?????????   ? ?       ?       ?                ? .gvfs
```

If it happens again, I'll be sure to try your suggestions...

Thanks for your time.

---

