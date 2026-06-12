---
title: "Problem with installer partitioning"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by tumble on 2009-04-27
Hi, I'm installing xubuntu 9.04 to my netbook via usb drive and once at the end of the installer having chosen partitions etc ( I selecected use the drive, it has xp on at the moment) I get this error:

The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

"/cdrom

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?"

So I try again and get the same error. I have no cdrom drive on my netbook, any ideas?

---

### Post by iaw4 on 2009-04-27
confirmed here, too, on an ibm s10e.

apparently, it thinks that the first sata device is a /cdrom, and mounts it as such.

it is impossible to unmount it.  I booted down to single user mode, and tried to unmount it.  this does not work, either.

this looks like a bug to me.

---

### Post by lkguigmv1 on 2009-08-05
Hi,I also get that error today when i tried to install x-ubuntu 9.04 on my portable external hardisk. .
After severral failures i decide to creat new partion table on the device (which will remove all partitions on the disk and also your data), then creat a new partion and install x-ubuntu on it . Finally this way work for me. I hope that this can reveal some helpful point for you.
Sory for my bad English.

---

