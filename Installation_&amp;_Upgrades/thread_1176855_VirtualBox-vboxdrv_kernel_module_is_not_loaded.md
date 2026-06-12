---
title: "VirtualBox-vboxdrv kernel module is not loaded"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by pHuXx on 2009-06-02
I updated to Jaunty and am getting this:

q@q-desktop:~$ sudo VirtualBox
[sudo] password for q: 
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
available for the current kernel (2.6.28-11-generic) or it failed to
load. Please recompile the kernel module and install it by

sudo /etc/init.d/vboxdrv setup

You will not be able to start VMs until this problem is fixed.

When i do sudo /etc/init.d/vboxdrv setup:

q@q-desktop:~$ sudo /etc/init.d/vboxdrv setup
* Stopping VirtualBox kernel module * done.
* Recompiling VirtualBox kernel module 
* Look at /var/log/vbox-install.log to find out what went wrong

So what should i do.
Please help.

---

### Post by zvacet on 2009-06-05
Go to the synaptic and reinstall VB.That should help.

---

