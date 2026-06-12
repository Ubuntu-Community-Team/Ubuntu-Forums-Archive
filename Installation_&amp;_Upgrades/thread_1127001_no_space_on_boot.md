---
title: "no space on /boot"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by heiNey on 2009-04-16
im trying to do a security update for my system..but apparently i dont have enough space on my /boot.

im currently running 2.6.24-23-generic.  my question is, can i safely delete all of the files that do not have 2.6.24-23 in the name to make some space?  (i wont delete grub or lost+found or memtest86+)

```


-rw-r--r--  1 root root  422667 2008-08-20 21:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-10-21 20:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  422838 2008-11-24 14:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root  422838 2009-04-01 18:17 abi-2.6.24-23-generic
-rw-r--r--  1 root root   80049 2008-08-20 21:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-10-21 20:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   80062 2008-11-24 14:47 config-2.6.24-22-generic
-rw-r--r--  1 root root   80051 2009-04-01 18:17 config-2.6.24-23-generic
drwxr-xr-x  2 root root    1024 2009-04-07 10:12 grub
-rw-r--r--  1 root root 7895897 2008-09-14 00:27 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7872355 2008-09-13 23:24 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7899864 2008-11-08 16:09 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7899896 2008-10-27 19:04 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7898024 2008-12-09 22:00 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7897614 2008-11-27 10:07 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root 7897367 2009-04-07 10:12 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7897956 2009-02-10 20:49 initrd.img-2.6.24-23-generic.bak
drwx------  2 root root   12288 2008-09-13 23:13 lost+found
-rw-r--r--  1 root root  103204 2007-09-28 03:06 memtest86+.bin
-rw-r--r--  1 root root  905170 2008-08-20 21:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-10-21 20:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  905617 2008-11-24 14:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root  905833 2009-04-01 18:17 System.map-2.6.24-23-generic
-rw-r--r--  1 root root 1921464 2008-08-20 21:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1920760 2008-10-21 20:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1921176 2008-11-24 14:47 vmlinuz-2.6.24-22-generic
-rw-r--r--  1 root root 1922520 2009-04-01 18:17 vmlinuz-2.6.24-23-generic


```

---

### Post by Partyboi2 on 2009-04-16
Open up Synaptic and do a search for 'linux-image' and remove all the old kernels you know longer need I would suggest keeping one as a backup as well as your current kernel.

---

### Post by heiNey on 2009-04-16
ok thanks...ill do that.

---

