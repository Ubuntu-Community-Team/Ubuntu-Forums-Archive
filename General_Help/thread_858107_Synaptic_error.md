---
title: "Synaptic error"
date: 2008-07-13
forum: General Help
---

### Post by emerc01 on 2008-07-13
In cleaning up my /boot I marked three old kernels for removal in Synaptic.  Two worked fine, the third seems to have been removed (it isn't in /lib/modules) but synaptic still thinks it has to remove it.  I can't figure out how to unmark it for removal.  some results:

```


sudo apt-get install -f

Removing linux-ubuntu-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Synaptic keeps trying to remove it.  Any solutions?

---

### Post by rraj.be on 2008-07-13
This is due to Presence fo broken package's....

Try to fix them form synaptic

---

### Post by drs305 on 2008-07-13
Try running the following.

```

sudo dpkg --purge linux-ubuntu-modules-2.6.22-14-generic

```

This may generate an error message something equivalent to:
```
Purging configuration files for linux-ubuntu-modules-2....
rm: cannot remove `/var/log/XXXXX': No such file or directory
dpkg: error processing acct (--purge):
```

If you get that message, please post the results.

---

### Post by emerc01 on 2008-07-18
Thank you for the suggestion.  I get the following error:

```
(Reading database ... 138560 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-generic

```

---

### Post by drs305 on 2008-07-19
emerc01,

Except for the previous suggestion by rraj.be to try to repair broken packages via synaptic, I'm hesitant to suggest a fix to this except to try to reinstall "linux-image-2.6.22-14-generic" and then remove it. 

One note if you try this: when installing a kernel, the install will ask if you want to use the installer's menu or continue using your old one. Choose to keep your old menu since you will be trying to uninstall this kernel shortly after installation.

The other thing you try is to remove the information for the troublesome package:
```

sudo rm /var/lib/dpkg/info/linux-ubuntu-modules-2.6.22-14*

```

---

