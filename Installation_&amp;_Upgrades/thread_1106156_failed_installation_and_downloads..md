---
title: "failed installation and downloads."
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by benon on 2009-03-25
r
E: _cache->open() failed, please report.
      
I get this message everytime i try to install any application,download updates, or open synaptic manager.I have run the following commands and this is what i got.Its not helping.

benon@benon-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege


benon@benon-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             143G   84G   52G  62% /
varrun               1009M  104K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   44K 1009M   1% /dev
devshm               1009M   24K 1009M   1% /dev/shm
lrm                  1009M   38M  972M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      143G   84G   52G  62% /home/benon/.gvfs

 
benon@benon-laptop:~$ ls -la /boot
total 11104
drwxr-xr-x  3 root root    4096 2009-03-07 06:58 .
drwxr-xr-x 21 root root    4096 2009-03-25 19:36 ..
-rw-r--r--  1 root root  422667 2008-06-18 21:11 abi-2.6.24-19-generic
-rw-r--r--  1 root root   80049 2008-06-18 21:11 config-2.6.24-19-generic
drwxr-xr-x  2 root root    4096 2009-03-07 06:58 grub
-rw-r--r--  1 root root 7880976 2009-03-07 06:58 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root  103204 2007-09-28 13:06 memtest86+.bin
-rw-r--r--  1 root root  905146 2008-06-18 21:11 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1920472 2008-06-18 21:11 vmlinuz-2.6.24-19-generic

benon@benon-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             143G   84G   52G  62% /
varrun               1009M  104K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   44K 1009M   1% /dev
devshm               1009M   24K 1009M   1% /dev/shm
lrm                  1009M   38M  972M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      143G   84G   52G  62% /home/benon/.gvfs

     

please help. And what is a superuser privilage anyway?

---

### Post by cariboo on 2009-03-25
Have you tried running:

```
sudo dpkg --configure -a
```

Jim

---

