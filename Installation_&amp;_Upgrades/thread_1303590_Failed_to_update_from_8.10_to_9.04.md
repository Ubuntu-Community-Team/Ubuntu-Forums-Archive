---
title: "Failed to update from 8.10 to 9.04"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by wikikie on 2009-10-28
Dear all,

Recently, I tried to update my netbook from ubuntu 8.10 to 9.04.
The update process was quite smooth.
But, after I reboot and open the update manager, it urges me to have a partial update.
The followings are the outcome:
[COLOR=Blue]
The following packages will be REMOVED:
  linux-restricted-modules-2.6.27-7-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2220kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 149650 files and directories currently installed.)
Removing linux-restricted-modules-2.6.27-7-generic ...
rmdir: failed to remove `/lib/modules/2.6.27-7-generic/volatile/': No such file or directory
FATAL: Could not open '/boot/System.map-2.6.27-7-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
Cannot find /lib/modules/2.6.27-7-generic
update-initramfs: failed for /boot/initrd.img-2.6.27-7-generic
dpkg: error processing linux-restricted-modules-2.6.27-7-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-restricted-modules-2.6.27-7-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

Acutally, I am not quite sure what have been happening around.
I am still in Ubuntu 8.10 now.
Would anyone give my some hints about the issue?
Thanks a lots!

Wik

---

