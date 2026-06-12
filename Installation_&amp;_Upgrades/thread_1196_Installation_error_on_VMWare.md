---
title: "Installation error on VMWare"
date: 2004-10-19
forum: Installation &amp; Upgrades
---

### Post by Nick on 2004-10-19
I'm considering installing Ubuntu on my DELL Inspiron 5150, but wanted to get a better idea of the current level of hardware support by installing it on a VMWare Virtual Machine beforehand.

Unfortunately, the base install fails. I was directed to terminal 3 where I found segmentation faults, etc. See:

> insmod /lib/modules/2.6.8.1-3-386/kernel/drivers/net/pcnet32.ko
  No matching physical volumes found
  No volume groups found
  Reading all physical volumes. This may take a while...
Selecting previously deselected package base-files.
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_3.0.16ubuntu6_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/base-files_3.0.16ubuntu6_i386.deb (--install):
  subprocess pre-installation script killed by signal (Segmentation fault)
Selecting previously deselected package base-passwd.
Unpacking base-passwd (from .../base-passwd_3.5.7_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/base-passwd_3.5.7_i386.deb (--install):
  subprocess pre-installation script killed by signal (Segmentation fault)

Is this a problem inherent with my decision to install it on VMWare? Or is something else amiss? I'm using the Warty RC ISO to install.

---

### Post by cybrjackle on 2004-10-19
Can't help much w/ vmware, but Dell's are normally pretty good with Linux.

A lot of Dell's can be found here.

[http://wiki.ubuntu.com/HardwareSupport](http://wiki.ubuntu.com/HardwareSupport)

Dell 5150 installs

[http://www.dfernando.com/dell_setup.html](http://www.dfernando.com/dell_setup.html)   (debian)

You can find more here:

[http://www.linux-on-laptops.com/dell.html](http://www.linux-on-laptops.com/dell.html)

---

### Post by Points on 2004-10-21
I'm seeing the exact same issue with VmWare...I've tried the stock configured machines, and custom ones, and still having the same problem where you are.  I'll post if I figure something out.

p.s., I've tried to install from the latest warty iso via:  burned cd, virtual cd, and the iso set as a cdrom in vmware...all showing the same error - which leads me to believe theirs an error with that particular package.


Points

---

### Post by Points on 2004-10-22
Finally got through a successful VMware install on a friends machine running VMware version 4.5.2.  The previous version I had problems with was 4.0.5.  I don't have access to other versions, so I can't discern whether this is just a 4.0.5 issue or not.  Set up the virtual machine for a generic Linux 2.6.x kernel and all should run fine.

Points

---

