---
title: "Mount in 8.04 LTS"
date: 2008-05-07
forum: Hardware
---

### Post by cigtoxdoc on 2008-05-07
I need a fool-proof way for myself and my Son to use CD-ROM drive and use the LS-120 drive w/o Ubuntu telling us we don't have the correct permissions and other nonsense.  My account is setup with administrator privileges.  My Son's is not.

We used to be able to do this, but fstab got wiped-out in upgrade.

JHL

---

### Post by EMCGFX on 2008-05-07
Edit your fstab file from console.
```
sudo gedit /etc/fstab
```

Place this line in it, anywhare:
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Also, do you have only one cdrom drive or two ?

---

### Post by jcwmoore on 2008-05-07
make sure your son has access rights to the CD-ROM, you can control that from 
System>Admin...>Users and Groups

---

### Post by cigtoxdoc on 2008-05-08
Thank you for your reply.  CD-ROM drive seems to be under control.  The problem is the LS-120 drive.  According to error messages only ROOT can mount or unmount drive.  Ubuntu will not let me change file permissions on media/SuperDisk.

So we have the ridiculous situation where only ROOT can mount or unmout the drive, and you cannot access ROOT from GNOME unless you open a terminal window.

So, here is the question.  What do I need to do so that any user with a login in and password can do anything he/she wishes with the LS-120 drive whether a standard floppy and/or SuperDisk is used?

---

