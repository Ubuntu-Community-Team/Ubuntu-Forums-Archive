---
title: "VirtualBox kernel driver not installed"
date: 2008-09-26
forum: General Help
---

### Post by Robotman on 2008-09-26
I'm trying to get virtualbox running, but I get the following message in my Xubuntu 8.04 installation:

```
VirtualBox kernel driver not installed. The vboxdrv kernel module 
was either not loaded or /dev/vboxdrv was not created for some reason.
 Please install the virtualbox-ose-modules package for your kernel, e.g. 
virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45} 
```

Does anybody know how to fix this and get VirtualBox up and running?

---

### Post by lewiz on 2008-09-27
first of all I'd really recommend you use the official Sun repo from [http://virtualbox.org/wiki/Linux_Downloads](http://virtualbox.org/wiki/Linux_Downloads)

remove your existing virtualbox packages and the install virtualbox-2

good luck

---

### Post by Robotman on 2008-09-27
Thanks for the link lewiz, I'll definitely check out v2 when I have more time.
For now, I found a fix to the kernel issue in [this thread](http://ubuntuforums.org/showthread.php?p=5653468).

---

