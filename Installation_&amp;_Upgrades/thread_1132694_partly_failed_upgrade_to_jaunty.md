---
title: "partly failed upgrade to jaunty"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by ways on 2009-04-22
hi

i upgraded my laptop to jaunty without problems. then i upgraded my media center. unfortunately it may have been an older version than intrepid. it only works partly now.

i can not boot a newer kernel than 2.6.24. newer kernels gives a grub error 24: Attempt to access block outside partition. i have checked the file system (ext3). i have removed and reinstalled kernels and modules. some applications doesnt work, like xbmc, elisa.

are there any options to a full reinstall? should i attempt a downgrade to intrepid?

---

### Post by yeats on 2009-04-22
There's not a way to downgrade, unfortunately...

There are logs in the /var/log directory that may point to what failed, including dpkg.log which shows a record of which packages got installed and which may have failed.  Syslog or dmesg may also have useful information (there are probably others that other folks can point you to).

Aside from this sort of troubleshooting, however, the only option is to reinstall.  Many users keep a separate /home partition and do fresh installs every time they upgrade, fwiw.

---

