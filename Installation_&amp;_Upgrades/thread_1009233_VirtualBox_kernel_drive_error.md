---
title: "VirtualBox kernel drive error"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by umarnasir on 2008-12-12
```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

I am running the latest version of Ubuntu and everything is updated

---

### Post by snova on 2008-12-12
Try installing the 'virtualbox-ose-source' package.

---

### Post by dragos_iliescu_2005 on 2008-12-12
Maybe this will help
[http://ubuntuforums.org/showthread.php?t=441004]("http://ubuntuforums.org/showthread.php?t=441004")

---

### Post by umarnasir on 2008-12-13
I already have 'virtualbox-ose-source' package.

and the link given there is kinda of outdated

---

### Post by snova on 2008-12-13
Ah, well, I don't know what to do then. But the VirtualBox package from their website worked for me without hassle, perhaps you should try that (but remove the ones you installed from the repos first). It also has USB support, which the OSE one does not.

---

