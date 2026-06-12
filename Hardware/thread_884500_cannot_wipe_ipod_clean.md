---
title: "cannot wipe ipod clean"
date: 2008-08-09
forum: Hardware
---

### Post by shoagun on 2008-08-09
I am having this peculiar problem where my ipod shuffle is shown to be at 100% copacity, but as far as I can tell there are no files on it.  In fact, I wanted to completely remove ALL files from the ipod. I went to the ipod directory (/media/IPOD) and used the command

```
rm -r *
```However, if I -right-click on the ipod icon on my desktop and chose properties, it is shown to be full.  

Also

```

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            378648432 108873572 250540640  31% /
varrun                 1028944        92   1028852   1% /var/run
varlock                1028944         0   1028944   0% /var/lock
udev                   1028944        96   1028848   1% /dev
devshm                 1028944         0   1028944   0% /dev/shm
lrm                    1028944     34696    994248   4% /lib/modules/2.6.22-15-generic/volatile
/dev/sdb               1981424   1974864      6560 100% /media/IPOD

```But when I go to the directory and check, I get:

```

$ ls -a
.  ..

```
Anyone have an idea of what's going on?

Thanks!

---

