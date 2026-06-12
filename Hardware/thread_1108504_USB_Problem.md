---
title: "USB Problem"
date: 2009-03-27
forum: Hardware
---

### Post by jonesjt on 2009-03-27
Good Evening all, 
   I am completely brand new to using Ubuntu and is has been some years since I used unix in general. I just installed Ubuntu 8.04 the Hardy Heron on my Dell Inspiron 1721 AMD 64bit laptop. I seem to have got most things up and running but I cant get any of my thumb drives to mount.

   The oddest part about the error is that on my GNOME desktop I can run an application that is sitting on the thumb drive, but when I try to open said drive to pull a file off of it GNOME says, "Unable to mount location".. "Can't mount file"

   If anyone can help me remedy this they would be awesome! Thank you so much.

---

### Post by sam1948 on 2009-03-27
type 
```
lsusb
```
and upload the results

---

### Post by jonesjt on 2009-03-28
```
ubuntu@ubuntu:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 004 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 004 Device 003: ID 413c:8126 Dell Computer Corp. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 006 Device 002: ID 154b:0016  
Bus 006 Device 001: ID 0000:0000  
```

Thank you for the reply.

---

### Post by sam1948 on 2009-03-28
sorry.
please make sure the usb disk is attached to the computer
try using usb that already proved to be working
and then
```
lsusb
```
and also upload also
```
ls /media
```
tell me if one of the disks is u'r usb drive
same for
```
 ls /dev/disk/by-label/
```
and last one
```
mount
```

upload all those 
and then remove the usb drive, run all those codes again and upload the results . try to do it organised so i'll know which output belongs to each command and with/without the usb disk plagued in.

bests

---

### Post by jonesjt on 2009-03-28
Here is the lsusb with a working usb thumbdrive:
```
ubuntu@ubuntu:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 004 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 004 Device 003: ID 413c:8126 Dell Computer Corp. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 005: ID 08ec:2039 M-Systems Flash Disk Pioneers 
Bus 006 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 006 Device 001: ID 0000:0000
```

Here is ls /media with same drive:
```
ubuntu@ubuntu:~$ ls /media
CSC212  KINGSTON

```

ls /dev/disk/by-label: Kingston is the usb that works
```
ubuntu@ubuntu:~$ ls /dev/disk/by-label/
KINGSTON
```

mount:
```
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/hda on /media/CSC212 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=999,utf8)
/dev/sdc1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

```

---

### Post by jonesjt on 2009-03-28
Same outputs without the working USB thumbdrive:

```
ubuntu@ubuntu:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 004 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 004 Device 003: ID 413c:8126 Dell Computer Corp. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 006 Device 001: ID 0000:0000 
```

```
ubuntu@ubuntu:~$ ls /media
CSC212
```  

```
ubuntu@ubuntu:~$ ls /dev/disk/by-label/
ls: cannot access /dev/disk/by-label/: No such file or directory

```


```
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/hda on /media/CSC212 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=999,utf8)

```

Thanks for all the help!

---

### Post by sam1948 on 2009-03-28
with the usb in.
type in the shell.
```
id
```
and upload results.
try:
```
ls /media/KINGSTON
```
and also
```
sudo ls /media/KINGSTON
```

---

### Post by jonesjt on 2009-03-28
```
loki@loki-laptop:~$ id
uid=1000(loki) gid=1000(loki) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),124(sambashare),1000(loki)
```

```
loki@loki-laptop:~$ ls media/KINGSTON
ls: cannot access media/KINGSTON: No such file or directory

```

```
loki@loki-laptop:~$ sudo ls /media/KINGSTON
[sudo] password for loki: 
ls: cannot access /media/KINGSTON: No such file or directory

```

NOTE: The problem is not with the Kingston Thumb Drive. It is with an Attache 16 GB Thumbdrive

---

### Post by sam1948 on 2009-03-29
I just hope all the work will be worth it (:

please re do these
[http://ubuntuforums.org/showpost.php?p=6970336&postcount=4](http://ubuntuforums.org/showpost.php?p=6970336&postcount=4)
with the non working usb attached
(if it was attached all along so remove it and re do)

---

