---
title: "Help with Rio Karma"
date: 2008-09-04
forum: Hardware
---

### Post by socngill on 2008-09-04
Hi guys.

I am trying to get my Karma to work via USB, but with little success.  I have been following the instructions here[http://jcconnor.wordpress.com/2007/02/11/my-karma-is-better-than-your-karma/]("http://jcconnor.wordpress.com/2007/02/11/my-karma-is-better-than-your-karma/") but when I install the OMFS driver I get the following errors:

> make -C /lib/modules/2.6.24-19-generic/build M=/home/neil/Desktop/omfs-0.8.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/neil/Desktop/omfs-0.8.0/inode.o
/home/neil/Desktop/omfs-0.8.0/inode.c: In function &#8216;omfs_iget&#8217;:
/home/neil/Desktop/omfs-0.8.0/inode.c:251: error: implicit declaration of function &#8216;iget_failed&#8217;
/home/neil/Desktop/omfs-0.8.0/inode.c: At top level:
/home/neil/Desktop/omfs-0.8.0/inode.c:283: error: &#8216;generic_show_options&#8217; undeclared here (not in a function)
/home/neil/Desktop/omfs-0.8.0/inode.c: In function &#8216;omfs_fill_super&#8217;:
/home/neil/Desktop/omfs-0.8.0/inode.c:416: error: implicit declaration of function &#8216;save_mount_options&#8217;
make[2]: *** [/home/neil/Desktop/omfs-0.8.0/inode.o] Error 1
make[1]: *** [_module_/home/neil/Desktop/omfs-0.8.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2

Can anybody help as I do not understand what is wrong or how to fix it.  Thanks.

Edit - should add that when I plug the Karma in and do the Dmesg i do get the sda: sda1 sda2 message - so the Kernel would appear to be fine.

---

