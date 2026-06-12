---
title: "YA dependency problem"
date: 2008-11-30
forum: General Help
---

### Post by owlcroft on 2008-11-30
On my laptop, I am running 8.04.1, upgraded from earlier versions; System Monitor shows me at Kernel 2.6.24-22-generic.

Looking in Synaptic, intending to do some cleanup, I find under "Not installed (residual config.)" an entry for linux-ubuntu-modules-2.6.22-14-generic and I want to delete it.

In /boot I have three kernel images--

initrd.img-2.6.22-15-generic
initrd.img-2.6.24-21-generic
initrd.img-2.6.24-22-generic

--each with its associated .bak, System.map, and vmlinuz files.  There is no 2.6.22-14 stuff whatever.

At Synaptic, if I select the "residual" module, mark it for total removal, and click Apply, after a bit it fails; the screen in full shows:

```
(Reading database ... 148214 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-generic ...
Purging configuration files for linux-ubuntu-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

And that's all she wrote.

Also, though, when marking the line, I get:

```
linux-ubuntu-modules-2.6.22-14-generic:

Package linux-ubuntu-modules-2.6.22-14-generic has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
```

The issue is not fatal, but I'd sure like to get this cruft off my system.  What's wrong, and how do I make it right?

Thanks.

---

