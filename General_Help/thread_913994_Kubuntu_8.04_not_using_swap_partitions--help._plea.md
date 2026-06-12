---
title: "Kubuntu 8.04 not using swap partitions--help. please"
date: 2008-09-08
forum: General Help
---

### Post by MikeB23930 on 2008-09-08
I have a multiboot system with two swap partitions.  My main stable OS, Kubuntu 8.04, is not using any swap space.  Two other OS's, Puppy Linux and Kubuntu 8.10 alpha 5, use both swap spaces.

My guess is that Kubuntu 8.04 doesn't recognize the swap spaces because their uuid's were changed when I installed Kubuntu 8.10.  The swapon man page says that swap is usually activate in the /etc/rc, but there is no such file in my Kubunty 8.10 root partition.

I would greatly appreciate it if some one could tell me how to get Kubuntu 8.04 to activate my swap spaces during bootup.

Thanks,

Mike

---

### Post by mikewhatever on 2008-09-08
Take a look at /etc/fstab. If uuid is the issue, fstab shoud be the place to correct it.

---

### Post by hyper_ch on 2008-09-08
change the UUID in the fstab accordingly.

find the UUID here in the /dev/disk/by-uuid folder
```

hyper@xubi:/$ cd /dev/disk/by-uuid/
hyper@xubi:/dev/disk/by-uuid$ ls -al
total 0
drwxr-xr-x 2 root root 240 2008-08-30 09:29 .
drwxr-xr-x 5 root root 100 2008-08-30 09:29 ..
lrwxrwxrwx 1 root root  23 2008-08-29 10:53 0e335a90-d3ad-4e79-9a9d-581c040bb459 -> ../../mapper/sda4_crypt
lrwxrwxrwx 1 root root  10 2008-08-29 10:53 247ad289-dbe5-4419-9965-e3cd30f0b080 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-08-29 10:53 24875c07-ce8a-4099-8cb8-88e56a6e6d29 -> ../../sdc2
lrwxrwxrwx 1 root root  23 2008-08-29 08:54 2cfd968d-5a2d-432b-a36d-f259a5839092 -> ../../mapper/sdc1_crypt
lrwxrwxrwx 1 root root  10 2008-08-29 10:53 6a636e05-c562-4d4b-b3fa-54dc3d3dda3c -> ../../sdd1
lrwxrwxrwx 1 root root  10 2008-08-29 10:53 7db6b61a-eab4-4451-a410-d7108c355191 -> ../../sdc4
lrwxrwxrwx 1 root root  10 2008-08-29 10:53 861C8E4F1C8E3A67 -> ../../sdc1
lrwxrwxrwx 1 root root  23 2008-08-29 08:54 91c3c5b6-c2af-4cf3-acbf-79f683d3413e -> ../../mapper/sdd1_crypt
lrwxrwxrwx 1 root root  23 2008-08-29 08:54 bf54d672-b3b1-4a09-8102-9c19dbc82bdc -> ../../mapper/sdb1_crypt
lrwxrwxrwx 1 root root  10 2008-08-29 10:53 f9ceb1b0-e084-4383-be4f-fc49b8f15545 -> ../../sda1
hyper@xubi:/dev/disk/by-uuid$

```

---

