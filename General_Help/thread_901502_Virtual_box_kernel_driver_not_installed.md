---
title: "Virtual box kernel driver not installed"
date: 2008-08-26
forum: General Help
---

### Post by josemaster2228 on 2008-08-26
helo am a newbe to ubuntu when i try to run a virtual machine i get the following problem 

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Código Resultado: 
0x80004005
Componente: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 i dont know how to fix it could you help me please thank you

---

### Post by jimv on 2008-08-26
You need to install the kernel drivers.  A command like this should work:

```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```

---

### Post by josemaster2228 on 2008-08-26
thank you alot it worked!!:KS

---

