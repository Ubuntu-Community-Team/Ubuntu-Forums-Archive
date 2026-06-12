---
title: "Virtual Box Stopped Working"
date: 2008-12-01
forum: General Help
---

### Post by dem0s on 2008-12-01
For some reason Virtual Box has stopped working and I'm now getting the same error I first got when I installed Virtual Box:

[I]VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).[/I]

When I try *sudo apt-get install virtualbox-ose-modules-generic virtualbox-ose* I get the following message *virtualbox-ose-modules-generic is already the newest version.*

Can anyone help with this? I'm running Kubuntu Hardy.

Thanks.

---

### Post by kanikilu on 2008-12-01
I'm not sure if this applies to your problem, but I had to recompile the virtualbox kernel modules after updating to the latest kernel:

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by binbash on 2008-12-01
Did you update your kernel lately?If so you have to re-install the kernel driver via sudo /etc/init.d/vboxdrv setup

---

### Post by dem0s on 2008-12-01
I Haven't updated my Kernel unless there was update that came through automatically. I tried typing *sudo /etc/init.d/vboxdrv setup* but I get the following response *Usage: /etc/init.d/vboxdrv {start|stop|restart|status}*.

I tried *sudo /etc/init.d/vboxdrv start* but get the following:
[I]
 * Starting VirtualBox kernel module vboxdrv
 * No suitable module for running kernel found.
[/I]

---

