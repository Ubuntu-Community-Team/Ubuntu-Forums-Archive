---
title: "Adaptec SAS"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by Ithium on 2006-08-24
Trying to install Ubuntu 6.06 on a IBM 206M. During the first part of the install it loads the aic94xx driver for the Adaptec controller but I am never able to see the hard drives.  I have been able to load CentOS 4.2 w/ the aic94xx driver and all works fine. I would prefer to install Ubuntu. Has anyone been able to successfully see the hard drives on this box?

---

### Post by artimador on 2006-08-25
I am having the same issue. I tried to modprobe libata and that didn't help. I am using an Xseries 306m. I've tried kubuntu but not anyother distro.

---

### Post by Mstar on 2006-08-30
This is a known bug see bug #46510 [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/46510]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/46510")

The installer works fine but when the system tries to boot from the hard disk it can not see the disk like bug #53138. [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53138]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/53138")

 I went ahead and added the modules to the initrd on the hard disk but I am stuck on editing conf/modules.

Has anybody else made any progress ?

---

### Post by edylie on 2006-11-02
I am on 306m and unable to install ubuntu 6.10 as well.
Cant see the drive!

*sigh*

---

