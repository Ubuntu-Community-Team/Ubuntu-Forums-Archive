---
title: "Help automounting NTFS external HD with read access"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by Roobert on 2006-11-01
Sigh.....could someone point me to a link on how to automount an external NTFS LaCie hard drive with read access? Currently, I have it mounted, but can't read it. I had read access set up before, but I reinstalled Dapper, overwriting my fstab.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /home           ext3    defaults        0       2
/dev/sda7       /media/dos      vfat    defaults,utf8,umask=007,gid=46 0       1/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/sdb1       /media/sdb1     ntfs    defaults,user 0 0
/dev/sda2       /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Output from mount:

```
$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
/dev/sda5 on /home type ext3 (rw)
/dev/sda7 on /media/dos type vfat (rw,utf8,umask=007,gid=46)
/dev/sda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on /media/windows type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sdb1 on /media/sdb1 type ntfs (rw,noexec,nosuid,nodev,user=epatton)
```

Note the external drive is mounted on /dev/sdb1.

I know it involves changing the permissions in the options section, but there are so many ways of doing this, it gets never confusing. I checked "Users and Groups" and I belong to groups root, plugdev, and users.

Thanks!

---

