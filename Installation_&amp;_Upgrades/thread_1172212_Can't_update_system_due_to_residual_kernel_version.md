---
title: "Can't update system due to residual kernel version"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by secret901 on 2009-05-28
I upgraded to 9.04 from 8.10 and now I'm having problem running the Update Manager (or installing any software for that matter). Running ```
sudo apt-get install -f
``` gives the following output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-12-generic
0 upgraded, 0 newly installed, 1 to remove and 111 not upgraded.
2 not fully installed or removed.
After this operation, 15.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 254386 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-12-generic ...
WARNING: Couldn't open directory /lib/modules/2.6.24-12-generic: No such file or directory
FATAL: Could not open /lib/modules/2.6.24-12-generic/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-12-generic
Cannot find /lib/modules/2.6.24-12-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-12-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-12-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-12-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It seems that Ubuntu thinks that I have the module linux-ubuntu-modules-2.6.24-12-generic installed and is trying to remove it, but can't since I don't really have it.  My /lib/modules/ directory has the following:
```

dhn@dell:~$ ls /lib/modules/
2.6.20-15-generic  2.6.24-12-386      2.6.24-16-generic  2.6.27-9-generic
2.6.20-16-generic  2.6.24-15-386      2.6.24-17-386	 2.6.28-11-generic
2.6.22-13-generic  2.6.24-15-generic  2.6.27-11-generic
2.6.22-14-generic  2.6.24-16-386      2.6.27-7-generic
```

I never added or removed anything to/from this directory.  I now can't update my computer or install anything because it always returns the error while trying to remove that nonexistent package first.

---

### Post by secret901 on 2009-05-28
Fixed.  I just created a symbolic link to one of the existing kernel directories.

---

### Post by lisati on 2009-05-28
This is just a thought, but wouldn't some people consider going from 9.04 to 8.10 a "downgrade"?

---

