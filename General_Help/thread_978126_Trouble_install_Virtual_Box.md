---
title: "Trouble install Virtual Box"
date: 2008-11-10
forum: General Help
---

### Post by Anditsu on 2008-11-10
Hello every one,
I have down loaded and installed the packages for virtual box with the apt tool,on Ubuntu 8.4 LTS and got the problem listed below


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by kernelhaxor on 2008-11-10
Try this in a terminal:

```
sudo aptitude install virtualbox-ose-modules-generic
```

Check out a similar thread: [http://ubuntuforums.org/showthread.php?t=737305](http://ubuntuforums.org/showthread.php?t=737305)

---

