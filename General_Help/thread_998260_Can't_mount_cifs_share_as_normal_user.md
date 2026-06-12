---
title: "Can't mount cifs share as normal user"
date: 2008-11-30
forum: General Help
---

### Post by djeikyb on 2008-11-30
So, this is pretty frustrating. I prefer to not login as root all the time. I also don't want to be sudo'ing every other command. I want my normal user account to be able to do common tasks like mount samba shares from work, and most immediately, my media storage/player device. My /etc/fstab line looks like this:```
//10.1.1.22/share    /media/popcorn    cifs    user=nmt,pass=1234,noauto    0 0
```

I read somewhere that my normal user must own the folder mounting to (/media/popcorn). So I ```
jake@daedalus:/media$ sudo chown jake:users popcorn/
jake@daedalus:/media$ chmod 777 popcorn/
jake@daedalus:/media$ ls -l
drwxr-xr-x 2 root root    48 2008-05-16 01:02 ipod/
drwxrwxrwx 2 jake users   48 2008-11-14 01:55 popcorn/
```

I read somewhere else I have to change /sbin/mount.cifs for some reason..```
root@daedalus:/sbin# chmod a+s /sbin/mount.cifs 
root@daedalus:/sbin# ls -l mount.cifs 
-rwsr-sr-x 1 root root 26540 2008-11-26 07:34 mount.cifs*
```

For those interested, this is the Popcorn Hour A110 device which I'm pretty happy with so far as a media player.

---

