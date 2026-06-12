---
title: "cant startx"
date: 2008-09-13
forum: General Help
---

### Post by eslam on 2008-09-13
hi guys 
i haved a problem with my ubuntu hardy heron 
when i powered on my pc i couldn't start my gnome as i recieved an error in my gdm

i logged into my shell and i tried to start my x window 
```
#startx
```

but i couldn't as i received this error 
> 
mktemp: can not create temp file /tmp/serverauth.oairoT5397:read only file system
/usr/bin/startx:line 139 can't create temp file for here do coment: read  only file system
xauth : error in locking authority file /home/eslam/.Xauthority
/usr/bin/startx:line 151 can't create temp file for here do coment: read  only file system

fatal server error: 
couldn't create lock file in /tmp/.txO-lock

giving up 
xinit: no such file or directory (errni2):unable to connect to x server
xinit : no such process (errno3) : server error
cauth: serror in locking authority file /home/eslam/.Xauthority 


so what is the problem and how to solve it

---

### Post by bodhi.zazen on 2008-09-13
Usually this problem is due to an error on the hard drive (and the partition was re-mounted read only).

The other possibility is that you changed the permissions of /tmp

Boot a live CD and run fsck (do not run this command on a mounted partition / running system).

```
sudo fsck -rfv /dev/sdxy 
```
 
        *** How to fsck: [http://www.linux.com/feature/32026](http://www.linux.com/feature/32026)

where "sdxy" is your root (or /tmp) partition.

---

