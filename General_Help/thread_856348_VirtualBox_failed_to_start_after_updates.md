---
title: "VirtualBox failed to start after updates"
date: 2008-07-11
forum: General Help
---

### Post by mikeyfbi on 2008-07-11
Hey guys,

I just did some updates and tried to load VirtualBox and got this:
```
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

so i ran this:
```
sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                                 
 * Look at /var/log/vbox-install.log to find out what went wrong
```

and then this is what /var/log/vbox-install.log says:
```

Makefile:70: Warning: using /usr/src/linux as the source directory of your Linux kernel. If this is not correct, specify KERN_DIR=<directory> and run Make again.
Makefile:76: *** Error: /usr/src/linux (version 2.6.22-14-rt) does not match the current kernel (version 2.6.22-15-rt).  Stop.
```

And I'm not sure what to make of the above :confused:

Any help is much appreciated! :)

Mike

---

### Post by sdennie on 2008-07-11
Looks like you are missing the headers for your running kernel.  I would try doing the following:

```

sudo apt-get install linux-headers-rt linux-headers-`uname -r`

```

That should grab the things you need to rebuild the virtualbox driver and insure that the next time you get a kernel update, it will grab the headers automatically.

---

### Post by tseven on 2009-02-04
I had the exact same problem.
sdennie, your fix was exactly what was needed.

After the somewhat lengthy update and reboot, my VirtualBox sprang back to llife.

Thank you very much. :D

---

