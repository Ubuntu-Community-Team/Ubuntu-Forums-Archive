---
title: "Can't install virtualbox 2.0 because of error"
date: 2008-09-19
forum: General Help
---

### Post by bcasanov on 2008-09-19
Hi,

If you could please help me, I would truly appreciate it, because I am confused as to how to fix this.  I followed the instructions from this site: [http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html) and this site where I obtained the virtualbox repository: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

After following through a prompt that told me to remove something old, I forgot what, and put in a command, /etc/init.d/vboxdrv setup, to reset something, I got the following error and I couldn't continue with the installation: 

 E: /var/cache/apt/archives/virtualbox-2.0_2.0.2-36488%5fUbuntu%5fhardy_i386.deb: trying to overwrite `/lib/modules/2.6.24-19-generic/misc/vboxdrv.ko', which is also in package virtualbox-ose-modules-2.6.24-19-generic

---

### Post by Therion on 2008-09-19
I'd remove everything Virtual Box related via Synaptic and try using [this tutorial](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html).  

It's worked for me several times now.

---

### Post by bcasanov on 2008-09-19
Thanks for the speedy reply!  I followed your suggestion, and I got Virtualbox to install!  The thing is, I can't see it in any of the menus.  Do you know how I might start it?

---

### Post by Therion on 2008-09-19
> **bcasanov said:**
> Thanks for the speedy reply!  I followed your suggestion, and I got Virtualbox to install!  The thing is, I can't see it in any of the menus.  Do you know how I might start it?
It should be under Applications/System Tools/Sun xVM VirtualBox.

---

### Post by rraj.be on 2008-09-19
> **bcasanov said:**
> Thanks for the speedy reply!  I followed your suggestion, and I got Virtualbox to install!  The thing is, I can't see it in any of the menus.  Do you know how I might start it?


It will be under

Applications --> System Tools In gnome

Else you can start this from terminal by typing

```
virtualbox
```

---

