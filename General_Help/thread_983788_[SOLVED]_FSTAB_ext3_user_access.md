---
title: "[SOLVED] FSTAB ext3 user access"
date: 2008-11-16
forum: General Help
---

### Post by rolodoom on 2008-11-16
Hello. I just bought a new drive 'cause I wanna switch into ubuntu. I formated my new drive using ext3 and tried to put it on my fstab. Then reboot and Surprise!!! I can write it but only as root, and not as a normal user.

Which is the correct line for fstab to mount a ext3 formated drive permanently with read/write access with my normal user account and not only as root???

I'm using ubuntu 8.10

---

### Post by taurus on 2008-11-16
You just need to change the ownership of the mount point for that drive from root to your login name.  Then, you can write to it anytime you want.  _Assuming_ your login name is doom and you mount that harddrive to /media/share, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo chown -R doom:doom /media/share
ls -la /media
```

---

### Post by rolodoom on 2008-11-16
Well, nothing. Still can write as user.  Here's my fstab, the problem is with /dev/sdc1:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=441a962c-9aad-420b-afef-f4980eee6585 /  ext3 relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=4ba326e4-9e2a-4449-9848-64edd59ba61e /home  ext3    relatime        0       2
# /dev/sdb5
UUID=d430d4dd-bef2-4b62-a4d8-be047a2e6e2a none    swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sdc1
# DATA
/dev/sdc1    /media/DATA    ext3    relatime    0    2

# /dev/sda1
# AUDIO
UUID=5CAC374FAC372346    /media/AUDIO ntfs nls=utf8,auto,user,fmask=0111,dmask=0000   0   0
```

---

### Post by taurus on 2008-11-16
Are we talking about /dev/sdc1?  I assume it is an external USB drive.  What's the output of this command?

```
ls -la /media
```

---

### Post by rolodoom on 2008-11-16
No it's not an external device, neither sda1. Both are internal SATA drives, I just mount them on /media 'cause I like the icon on desktop.

The outpu for:
```
ls -la /media
```is
```
total 20
drwxr-xr-x  5 root root 4096 2008-11-16 03:28 .
drwxr-xr-x 20 root root 4096 2008-11-15 19:24 ..
drwxrwxrwx  1 root root 4096 2008-11-10 19:59 AUDIO
lrwxrwxrwx  1 root root    6 2008-11-15 19:11 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-11-15 19:11 cdrom0
drwxr-xr-x  3 root root 4096 2008-11-16 01:38 DATA
-rw-r--r--  1 root root    0 2008-11-16 03:28 .hal-mtab

```The disk is mounted but only can access it using root. I unmounted
```
sudo umount /media/DATA
ls -la /media
```and then:
```
total 20
drwxr-xr-x  5 root     root     4096 2008-11-16 03:28 .
drwxr-xr-x 20 root     root     4096 2008-11-15 19:24 ..
drwxrwxrwx  1 root     root     4096 2008-11-10 19:59 AUDIO
lrwxrwxrwx  1 root     root        6 2008-11-15 19:11 cdrom -> cdrom0
drwxr-xr-x  2 root     root     4096 2008-11-15 19:11 cdrom0
drwxr-xr-x  2 rolodoom rolodoom 4096 2008-11-16 02:54 DATA
-rw-r--r--  1 root     root        0 2008-11-16 03:28 .hal-mtab

```As you can see, I did change the ownership for the folder /media/DATA

---

### Post by taurus on 2008-11-16
Personally, I would make the entry for /dev/sdc1 in /etc/fstab to look like this.

```
/dev/sdc1    /media/DATA    ext3    **defaults**    0    2
```

---

### Post by rolodoom on 2008-11-16
Dude, already change it and nothing. What's wrong? don't get it.

---

### Post by taurus on 2008-11-16
After making a change in /etc/fstab, did you reboot?  

Can you post the outputs of these commands from a terminal again?

```
cat /etc/fstab
mount
ls -la /media
id
```

---

### Post by rolodoom on 2008-11-16
> rolodoom@rolo:~$ cat /etc/fstab```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=441a962c-9aad-420b-afef-f4980eee6585 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=4ba326e4-9e2a-4449-9848-64edd59ba61e /home           ext3    relatime        0       2
# /dev/sdb5
UUID=d430d4dd-bef2-4b62-a4d8-be047a2e6e2a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sdc1
# DATA
UUID=2cbd797f-451a-42fb-837b-5a548a80fa59    /media/DATA    ext3    defaults    0    2

# /dev/sda1
# AUDIO
UUID=5CAC374FAC372346    /media/AUDIO    ntfs    nls=utf8,auto,user,fmask=0111,dmask=0000   0   0

```> rolodoom@rolo:~$ mount```
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb2 on /home type ext3 (rw,relatime)
/dev/sdc1 on /media/DATA type ext3 (rw)
/dev/sda1 on /media/AUDIO type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rolodoom/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rolodoom)

```> rolodoom@rolo:~$ ls -la /media```
 total 20
drwxr-xr-x  5 root root 4096 2008-11-16 04:02 .
drwxr-xr-x 20 root root 4096 2008-11-15 19:24 ..
drwxrwxrwx  1 root root 4096 2008-11-10 19:59 AUDIO
lrwxrwxrwx  1 root root    6 2008-11-15 19:11 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-11-15 19:11 cdrom0
drwxr-xr-x  3 root root 4096 2008-11-16 01:38 DATA
-rw-r--r--  1 root root    0 2008-11-16 04:02 .hal-mtab

```> rolodoom@rolo:~$ id```
uid=1000(rolodoom) gid=1000(rolodoom) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(rolodoom)
```

---

### Post by taurus on 2008-11-16
Will see if it sticks this time.

```
sudo chown -R rolodoom:rolodoom /media/DATA
ls -la /media
```

---

### Post by rolodoom on 2008-11-16
Yeah!!!  Nowcan access as user. So I think I didn't chown the folder /media/DATA as I thought

Thanks

:guitar:

---

### Post by caue.rego on 2009-07-17
better use: **sudo chmod 777 /media/DATA**

don't need to change fstab, can leave it as defaults or relatime whatever, don't need to be inside /media (I like to leave it for media auto mounted by the system).

in a step by step:

- **sudo blkid** - find the UUID of, let's say, /dev/sda1, unless you want to leave it as /dev/sda1
- **sudo gedit /etc/fstab** - or use **nano**
- add the line **UUID=xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxxxxxxx /DATA ext3 relatime 0 2** - or use **defaults** (I don't know what is the dump 0 and pass 2)
- **sudo mkdir /DATA**
- **sudo mount /DATA**
- **sudo chmod 777 /media/DATA**

and it should work on boot as well.

---

