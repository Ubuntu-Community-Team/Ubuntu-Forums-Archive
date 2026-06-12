---
title: "virtualbox ose"
date: 2008-10-22
forum: General Help
---

### Post by michael@cgl on 2008-10-22
hi when trying to set up virtual box ose, to run win xp, it tells me:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

how do i remedy this ?




ps complete beginner to computers

---

### Post by baju on 2008-10-22
You have to install the kernel modules in order to use VBox.
The name of the package depends on the kernel you use. If you use the generic kernel 2.6.24-21 ( default ) you have to install the package virtualbox-ose-modules-2.6.24-21-generic . Reboot after install and it will work.
If you don't know which package you need, please post the name of kernel image you use.

---

### Post by Joeb454 on 2008-10-22
I think you have to run ```
sudo /etc/init.d/vboxdrv setup
``` To compile the kernel module for VirtualBox :)

---

### Post by LostInBrittany on 2008-11-04
> **Joeb454 said:**
> I think you have to run ```
sudo /etc/init.d/vboxdrv setup
``` To compile the kernel module for VirtualBox :)

When I try to do it, it tells me :
```
~$  sudo /etc/init.d/vboxdrv setup
* Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
```

I have no idea of why, and I am unable to find an answer in the forum. Any ideas ?

Thanks in advance !

---

### Post by baju on 2008-11-05
Actually sudo /etc/init.d/vboxdrv setup will not work since /etc/init.d/vboxdrv initates the vboxservice and works only with the parameters start,stop,restart or status. You can try ```

sudo /etc/init.d/vboxdrv start

```
to start the driver.

However you shouldn't have to call this at all because Ubuntu provides compiled kernel modules and initiates the driver automatically.

---

### Post by detroit/zero on 2008-11-05
You have to add yourself to the vboxusers group```
sudo usermod -G vboxusers -a *USERNAME*
```and then run the setup command```
sudo /etc/init.d/vboxdrv setup
```I'm not sure why, but it has to be done in that order, otherwise it never works.

---

