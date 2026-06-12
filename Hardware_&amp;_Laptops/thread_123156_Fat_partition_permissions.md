---
title: "Fat partition permissions"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by jonathanm on 2006-01-29
Hi,

I'm having some problems with my fat partitions, they all belong to root on startup.  They are also read only to non root users.  However, because i set the fstab to users on all of them i can umount and mount them and then they come up with me as the owner.  I would really like them to be mine when they are mounted on startup instead of roots as then i can do my schoolwork without any hassle.  Thanks

Jonathan

:p

---

### Post by glinsvad on 2006-01-29
I'm assuming you've already changed the line in /etc/fstab
```
/dev/hda3       /media/myfatdrive  vfat    defaults        0       2
```
into
```
/dev/hda3       /media/myfatdrive  vfat    rw        0       0
```

You need to gain ownership of all the files on your fat-drive:
```
sudo chown -R $USER:$USER /media/myfatdrive 
```

---

### Post by jonathanm on 2006-01-29
no i changed it to:

```
/dev/hda10  /mnt/hda/Documents vfat users 0 0
```
and i have tried to chown, it comes up with operation not permitted
the problem is that whenever the drives are mounted using init scripts it is root who mounts them, i want to change this so that i mount them on init

---

### Post by lha on 2006-01-29
[QUOTE=jonathanm]no i changed it to:

```
/dev/hda10  /mnt/hda/Documents vfat users 0 0
```
and i have tried to chown, it comes up with operation not permitted
the problem is that whenever the drives are mounted using init scripts it is root who mounts them, i want to change this so that i mount them on init[/QUOTE]

Try
```
/dev/hda10  /mnt/hda/Documents vfat users,uid=jonathanm,dmask=022,fmask=133 0 0
``` You don't need that users part for rw access. It just lets non-root users mount and umount hda10.

---

### Post by aysiu on 2006-01-29
```
/dev/hda10  /mnt/hda/Documents vfat iocharset=utf8,umask=000 0 0
``` has always worked for me...

---

