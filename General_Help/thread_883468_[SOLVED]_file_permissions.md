---
title: "[SOLVED] file permissions"
date: 2008-08-08
forum: General Help
---

### Post by harryliddic on 2008-08-08
I just installed a new second hard drive for videos only. I followed the Ubuntu installation directions which included a** chown -R ** command and it won't let a program from the original hard drive write to it. How do I change the permission so that anyone or anything can read and write to this drive named /media/videos/  ?

---

### Post by p_quarles on 2008-08-08
Well, first post the output of these commands:
```
ls -la /media/videos
```
and
```
mount
```

---

### Post by harryliddic on 2008-08-08
> **p_quarles said:**
> Well, first post the output of these commands:
```
ls -la /media/videos
```
and
```
mount
```
harry@harry-desktop:~$ ls -la /media/videos
total 36
drwxr-xr-x  5 harry harry  4096 2008-08-07 20:23 .
drwxr-xr-x 11 root  root   4096 2008-08-07 19:29 ..
-rw-------  1 harry harry    49 2008-08-07 12:56 .directory
drwxr-xr-x  2 root  root   4096 2008-08-07 20:23 golf_video
drwx------  2 harry harry 16384 2008-08-05 20:19 lost+found
drwxr-xr-x  5 harry harry  4096 2008-08-07 21:24 tmp
harry@harry-desktop:~$ 

harry@harry-desktop:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/videos type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/harry/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=harry)
harry@harry-desktop:~$

---

### Post by p_quarles on 2008-08-08
Hmm. Everything there looks good (except for the fact that "golf_video" is owned by root). What program is it that can't write to it? Can other programs be used to write to that drive?

---

### Post by harryliddic on 2008-08-08
QDVDauthor and all the files I moved from that drive to my main one have write permission denied. Kino wrote to that drive when I was using files that were already on it. Can I change the golf_video from root?

---

### Post by p_quarles on 2008-08-08
Hmm. I wonder what the perms on the top-level of the drive are. Try:
```
ls -l /media | grep videos
```
and post the results again.

---

### Post by harryliddic on 2008-08-08
harry@harry-desktop:~$ ls -l /media | grep videos
drwxr-xr-x 5 harry harry 4096 2008-08-07 20:23 videos
harry@harry-desktop:~$

---

