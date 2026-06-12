---
title: "CD drive not opening"
date: 2008-08-15
forum: General Help
---

### Post by Stoodle on 2008-08-15
My CD drive isn't opening. 

Eject:
```

eject: tried to use `/dev/hdc' as device name but it is no block device
eject: unable to find or open device for: `cdrom'

```fdisk -l:nothing

```

 lsof /dev/cdrom
lsof: status error on /dev/cdrom: No such file or directory
lsof 4.78
 latest revision: ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/
 latest FAQ: ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ
 latest man page: ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man
 usage: [-?abhlnNoOPRstUvVX] [+|-c c] [+|-d s] [+D D] [+|-f]
 [-F [f]] [-g [s]] [-i [i]] [+|-L [l]] [+m [m]] [+|-M] [-o [o]]
 [-p s] [+|-r [t]] [-S [t]] [-T [t]] [-u s] [+|-w] [-x [fl]] [--] [names]
Use the ``-h'' option to get more help information.

``````

 lsof /dev/cdrom0
lsof: status error on /dev/cdrom0: No such file or directory
lsof 4.78
 latest revision: ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/
 latest FAQ: ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ
 latest man page: ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man
 usage: [-?abhlnNoOPRstUvVX] [+|-c c] [+|-d s] [+D D] [+|-f]
 [-F [f]] [-g [s]] [-i [i]] [+|-L [l]] [+m [m]] [+|-M] [-o [o]]
 [-p s] [+|-r [t]] [-S [t]] [-T [t]] [-u s] [+|-w] [-x [fl]] [--] [names]

``````

 mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda2 on /media/hda2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

```

---

### Post by Koala Kid on 2009-09-04
in case you don't give to "eject" any parameters, it works directly with /dev/hdc.
just locate your cd/dvd drive with:

```
ls /dev/cd*
ls /dev/dvd*
```

and give it to "eject".
in my case:
```
eject /dev/dvd2
```

---

### Post by DariaJun on 2009-10-02
> **Koala Kid said:**
> in case you don't give to "eject" any parameters, it works directly with /dev/hdc.
just locate your cd/dvd drive with:

```
ls /dev/cd*
ls /dev/dvd*
```

and give it to "eject".
in my case:
```
eject /dev/dvd2
```

I'm having the exact same problem and getting the same error code as was quoted, and when I entered 

ls /dev/cd* 

it gave me

ls: cannot access /dev/cd: No such file or directory

Thought I might as well just try for the hell of it 

eject /dev/cd

and it just came back at me with 

eject: unable to find or open device for: '/dev/cd'

This happened after I tried to originally eject the cd and it failed, after which I rebooted and now the cd no longer exists in the system. I'm hoping it is not a hardware failure, this is quite an old laptop (IBM thinkpad 600x). Using Ubuntu 9.04.

---

### Post by DariaJun on 2009-10-02
Weird, it fixed itself after a hard reboot. I'd still be interested to see what your response is since I wouldn't be surprised if I run into this again.

---

