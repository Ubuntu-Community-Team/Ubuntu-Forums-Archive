---
title: "[SOLVED] apt-get bad state"
date: 2008-10-25
forum: General Help
---

### Post by joebodo on 2008-10-25
I used the new system cleaner to remove some old kernels. Part way through the removals, the system cleaner crashed.

Now, whenever I try to use apt, I get the following error:

$ **sudo apt-get  -f remove linux-ubuntu-modules-2.6.24-20-eeepc**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  debhelper intltool-debian po-debconf binutils-static gettext nvidia-kernel-common linux-restricted-modules-common html2text
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-20-eeepc
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 15.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 113745 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-20-eeepc ...
FATAL: Could not open '/boot/System.map-2.6.24-20-eeepc': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-20-eeepc
Cannot find /lib/modules/2.6.24-20-eeepc
update-initramfs: failed for /boot/initrd.img-2.6.24-20-eeepc
dpkg: error processing linux-ubuntu-modules-2.6.24-20-eeepc (--remove):
 subprocess post-removal script returned error exit status 1
[B]Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-20-eeepc[/B]
E: Directory '/var/log/apt/' missing
E: Sub-process /usr/bin/dpkg returned an error code (1)

Is there a way to resolve this problem? I cannot add new software or update my system.

Thanks

---

### Post by unutbu on 2008-10-25
Notice these errors:
```
Could not open '/boot/System.map-2.6.24-20-eeepc': No such file or directory
Cannot find /lib/modules/2.6.24-20-eeepc
E: Directory '/var/log/apt/' missing
```

The APT system is rather finicky when removing packages. 
It runs a script which tells it which files and directories to remove.
If a file or directory is missing, it aborts. 

To trick the APT system into thinking the files/dirs are still there:

Try
```

sudo touch /boot/System.map-2.6.24-20-eeepc
sudo mkdir /lib/modules/2.6.24-20-eeepc
sudo mkdir /var/log/apt/
```

If you get similar errors, try doing
```

sudo touch FILE
```

to create a dummy file

or ```


sudo mkdir DIR
```

to create a dummy dir.

---

### Post by joebodo on 2008-10-25
That worked! Thanks for the help.

---

