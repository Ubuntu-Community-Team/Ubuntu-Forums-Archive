---
title: "[SOLVED] broken package"
date: 2008-10-07
forum: General Help
---

### Post by iRPM on 2008-10-07
Hi,

my problem is:

```
sergejus@sergejus-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-15-generic
0 upgraded, 0 newly installed, 1 to remove and 13 not upgraded.
1 not fully installed or removed.
After this operation, 9966kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 183689 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-15-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-15-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-15-generic
Cannot find /lib/modules/2.6.22-15-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-15-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-15-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-15-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried to remove it and also reinstall the package from the .deb. It says to run 'sudo apt-get install -f'. So, no results

My system is:
```
uname -a
Linux sergejus-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
```

---

### Post by bapoumba on 2008-10-07
It's probably a bad leftover from an upgrade (did you upgrade or fresh install ?).

You can, as you are running 2.6.24-19, tweak the bad 2.6.22-15-generic postrm code so that dpkg does not see it any longer:
```
gksudo gedit /var/lib/dpkg/info/linux-ubuntu-modules-2.6.22-15-generic.postrm
```
and replace what is there by:
```
#!/bin/bash
exit 0
```
Then:
```
sudo dpkg --purge linux-ubuntu-modules-2.6.22-15-generic
```

---

### Post by iRPM on 2008-10-08
Thanks a lot,

The purge of the the package was successful

 :)

---

### Post by bapoumba on 2008-10-08
Cool :)
Please do not hesitate if you have any further question (I might not be able to answer though, but there are lots of very knowledgeable people around here).

---

