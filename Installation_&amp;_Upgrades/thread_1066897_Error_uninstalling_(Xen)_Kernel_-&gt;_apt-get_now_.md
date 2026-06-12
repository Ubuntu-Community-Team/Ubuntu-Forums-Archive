---
title: "Error uninstalling (Xen) Kernel -&gt; apt-get now working anymore"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by Termi11 on 2009-02-11
Hello,
i have a problem uninstalling a Kernel (xen) from my system:

> root@nas:/home/dirk# dpkg --remove --force-remove-reinstreq linux-ubuntu-modules-2.6.24-19-xen linux-image-2.6.24-19-xen
(Reading database ... 78179 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-19-xen ...
FATAL: Could not open '/boot/System.map-2.6.24-19-xen': No such file or directory
/usr/sbin/update-initramfs: 516: awk: Permission denied
dpkg: error processing linux-ubuntu-modules-2.6.24-19-xen (--remove):
 subprocess post-removal script returned error exit status 126
dpkg - warning: ignoring request to remove linux-image-2.6.24-19-xen, only the config
 files of which are on the system.  Use --purge to remove them too.
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-xen
root@nas:/home/dirk# dpkg --remove --force-remove-reinstreq --purge linux-ubuntu-modules-2.6.24-19-xen linux-image-2.6.24-19-xen
dpkg: conflicting actions -P (--purge) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
root@nas:/home/dirk# apt-get remove --purge linux-ubuntu-modules-2.6.24-19-xen linux-image-2.6.24-19-xen
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-image-2.6.24-19-xen is not installed, so not removed
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-19-xen
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 9564kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 78179 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-19-xen ...
FATAL: Could not open '/boot/System.map-2.6.24-19-xen': No such file or directory
/usr/sbin/update-initramfs: 516: awk: Permission denied
dpkg: error processing linux-ubuntu-modules-2.6.24-19-xen (--remove):
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-xen
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@nas:/home/dirk# touch /boot/System.map-2.6.24-19-xen
root@nas:/home/dirk# apt-get remove --purge linux-ubuntu-modules-2.6.24-19-xen linux-image-2.6.24-19-xen
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-image-2.6.24-19-xen is not installed, so not removed
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-19-xen
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 9564kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 78179 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-19-xen ...
/usr/sbin/update-initramfs: 516: awk: Permission denied
dpkg: error processing linux-ubuntu-modules-2.6.24-19-xen (--remove):
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-xen
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@nas:/home/dirk# apt-get remove --purge linux-ubuntu-modules-2.6.24-19-xen linux-image-2.6.24-19-xen
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-image-2.6.24-19-xen is not installed, so not removed
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-19-xen
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 9564kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 78179 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-19-xen ...
/usr/sbin/update-initramfs: 516: awk: Permission denied
dpkg: error processing linux-ubuntu-modules-2.6.24-19-xen (--remove):
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-xen
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@nas:/home/dirk#


Because of this error, i can't install any other packages anymore.
Also tried in aptitude :

> root@nas:/boot# aptitude
(Reading database ... 78179 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-19-xen ...
/usr/sbin/update-initramfs: 516: awk: Permission denied
dpkg: error processing linux-ubuntu-modules-2.6.24-19-xen (--remove):
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-xen
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.

How can i fix this error?
Ubuntu 8.04 (not all updates yet)

THANKS!

---

