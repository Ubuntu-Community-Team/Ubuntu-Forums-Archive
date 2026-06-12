---
title: "Package that isn't there marked for removal"
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

