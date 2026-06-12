---
title: "Virutal box"
date: 2008-09-08
forum: General Help
---

### Post by dragos240 on 2008-09-08
I need help. I keep getting this error every time i try to emulate inteped ibex 8.10.

```


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```Please help :confused: Im very confused.

---

### Post by Elfy on 2008-09-08
There are problems with ibex in virtual box -  [http://www.ubuntu.com/testing/intrepid/alpha5](http://www.ubuntu.com/testing/intrepid/alpha5)
> The Intrepid 2.6.27-2 kernel fails to boot as a Guest under VirtualBox. This issue is expected to be resolved for Intrepid Alpha 6. [https://bugs.launchpad.net/bugs/246067](https://bugs.launchpad.net/bugs/246067)

---

