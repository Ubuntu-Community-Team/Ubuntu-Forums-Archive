---
title: "i just did upgrade and now i can't install any software"
date: 2008-10-19
forum: General Help
---

### Post by aprilie on 2008-10-19
hi after my update ubuntu 8.04 i can not install any software my computer sad:
E: /var/cache/apt/archives/xulrunner-1.9_1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1_i386.deb: failed in buffer_write(fd) (10, ret=-1)
after that I tried to do upgrade again and it sad
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
if any one can give me an advise please help i did not make a backups

---

### Post by ghost_ryder35 on 2008-10-19
did you run
```

dpkg --configure -a

```
?

---

### Post by kostkon on 2008-10-19
To correct the above poster, you should do a
```
sudo dpkg --configure -a
```

It will ask you for a password, give yours.

---

### Post by ghost_ryder35 on 2008-10-19
> **kostkon said:**
> To correct the above poster, you should do a
```
sudo dpkg --configure -a
```It will ask you for a password, give yours.
yes you will need root permissions to run dpkg --configure -a

---

### Post by aprilie on 2008-10-19
i did run it and what is reply
valeriu@valeriu-laptop:~$ sudo dpkg --configure -a
dpkg: failed to write status record about `libgpod-common' to `/var/lib/dpkg/status': No space left on device

---

### Post by ghost_ryder35 on 2008-10-19
what is the output of
```

df -h

```

---

### Post by aprilie on 2008-10-19
valeriu@valeriu-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  3.7G     0 100% /
varrun               1009M   88K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   48K 1009M   1% /dev
devshm               1009M   12K 1009M   1% /dev/shm
/dev/sda4              71G   49G   22G  70% /media/sda4
overflow              1.0M   48K  976K   5% /tmp
but i have a lot of space on my sda3 partition

---

### Post by ghost_ryder35 on 2008-10-19
your file system is full... log on and remove some file's off of /dev/sda1, which is the root filesystem
/dev/sda1             3.7G  3.7G     0 100% /

---

### Post by ghost_ryder35 on 2008-10-19
oh yea, you will need root permissions to do so, so sudo you will need

---

### Post by aprilie on 2008-10-19
i did it by deleting ekiga and after that was the same
or to try it again by deleting samethink else?

---

### Post by ghost_ryder35 on 2008-10-19
keep deleting unimportant things until df -h shows sda1 less than 95%

---

### Post by aprilie on 2008-10-19
ok i will try but i do this in recovery mode like i did with ekiga  because sudo reply this
valeriu@valeriu-laptop:~$ sudo dpkg -r evolution
[sudo] password for valeriu: 
dpkg: dependency problems prevent removal of evolution:
 evolution-plugins depends on evolution (>= 2.22.1).
 evolution-exchange depends on evolution (>= 2.22.1).
dpkg: error processing evolution (--remove):
 dependency problems - not removing
dpkg: failed to write available record about `libhsqldb-java' to `/var/lib/dpkg/available': No space left on device
valeriu@valeriu-laptop:~$

---

### Post by aprilie on 2008-10-19
I install ubuntu 7.10

---

