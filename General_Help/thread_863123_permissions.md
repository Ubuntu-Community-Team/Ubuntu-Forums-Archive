---
title: "permissions"
date: 2008-07-18
forum: General Help
---

### Post by albonatto on 2008-07-18
Hi, 
I have installed ubuntu 8.04 in my laptop (Acer Aspire 5920) and I need to change all permission recursively in directory: /media/DATOS. So I try: 
Themis /media=>sudo chown -R -v luciana DATOS/
[sudo] password for luciana: 

and then I try

Themis /media=>ls -la
 total 16
drwxr-xr-x  4 root root 4096 2008-07-18 09:45 .
drwxr-xr-x 23 root root 4096 2008-07-08 15:26 ..
lrwxrwxrwx  1 root root    6 2008-07-08 16:42 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-07-08 16:42 cdrom0
dr-xr-xr-x  1 root root 4096 2008-07-18 12:43 DATOS
-rw-r--r--  1 root root    0 2008-07-18 09:45 .hal-mtab

but the vervose mode tell me that the permission is changed. Then I try to create a directory in DATOS and I have no permission. 

Thanks, 
Luciana

---

### Post by mkokotovich on 2008-07-18
What type of filesystem is DATOS?  I assume that because it is in /media it is some sort of external device.  I don't know that much about this area, but my guess is that maybe that filesystem doesn't support permissions.  Try making a test directory in your home directory, make some files and sub-directories, and try chown -R on that directory.  Change it to root and then back again. If that works, it is probably the FS on DATOS.

---

### Post by albonatto on 2008-07-18
I try the same in the root directory, create a directory and change permission, now it works. So you were rigth. 
DATOS is a NTFS partition mounted by wubi automatically on /dev/sda5.
How can I mount this partition in the root directory as an scratch?. 
Thanks

---

### Post by chrisccoulson on 2008-07-18
Could you please post your /etc/fstab?

---

### Post by albonatto on 2008-07-18
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda5	/media/DATOS	ntfs nls=utf8,umask=0222 0	0

---

### Post by chrisccoulson on 2008-07-18
The problem is you're using the read only NTFS driver. You need to use the ntfs-3g driver, which offers read/write support. Try this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro 0 1
/host/ubuntu/disks/boot /boot none bind 0 0
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
[COLOR="Red"]/dev/sda5 /media/DATOS ntfs-3g defaults,umask=0000 0 0[/COLOR] 
```

This will mount the partition with the ntfs-3g driver, and give full read-write support for everybody (if that is what you want)

---

### Post by haegl on 2008-07-18
You can't change the owner of a mounted ntfs partition. You can change the owner inside fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro 0 1
/host/ubuntu/disks/boot /boot none bind 0 0
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda5 /media/DATOS ntfs nls=utf8,umask=0222,[COLOR="Red"]uid=1001[/COLOR] 0 0
```

---

### Post by albonatto on 2008-07-18
mil gracias!!= thank you very much, it works!!

---

