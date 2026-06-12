---
title: "usb access rights problem"
date: 2014-05-29
forum: Hardware
---

### Post by freni on 2014-05-29
Hello fellow Ubuntu users,

I run Ubuntu 14.04 LTS (latest updates installed)
[B]
The Problem:[/B]
I mount my usb dirve from which im supposed to be able to start some sort of embedded program.

At First nothing happend at all, but I managed to manipulate /etc/fstab to be able to make the program to produce this error.

**The Error:**
```

Could not display “program”.
There is no application installed for “executable” files.
Do you want to search for an application to open this file?

```

What i found on this Error, was about access-rights so i tried to change them.

**So Far I:**
1. Tried to make a udev rule...> something went wrong and i could use my keyboard any more. Well fixed again, but I didn't went any deeper into this udev stuff.
2. Tried to chmod the Device ore Files, but its a read-only USB, so didn't work.
3. changed fstab to:```
 /dev/sr0 /media/user/device iso9660 ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,,mode=0666,dmode=0500,uhelper=udisks2 0 0
```
Here i took the options from the device when it mounts by itself and only modified "mode" i also tried 0777 and dmode to 0777 and more or less all the options i could find.

The Device mounts right:
```
[FONT=courier new]foo@bar:/$ mount
/dev/sr0 on /media/foo/device type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,uhelper=udisks2)[/FONT]
```

The user is ok too:
```
foo@bar:/$ id
uid=1000(foo) gid=1000(foo) groups=1000(foo),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare)
```

Every help or direction i could search for, would be highly appreciated.

---

### Post by freni on 2014-05-30
Seems to be a compatibility Problem. So its waiting time.

---

### Post by gordintoronto on 2014-05-30
It's easier to help, if you provide specifics, such as the name of the program you are trying to run from the flash drive.

---

