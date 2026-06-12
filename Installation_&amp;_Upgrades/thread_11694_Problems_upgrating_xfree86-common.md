---
title: "Problems upgrating xfree86-common"
date: 2005-01-18
forum: Installation &amp; Upgrades
---

### Post by VaDor on 2005-01-18
I used the apt-get dist-upgrade after i update the error above show, then I forced the package xfree86-common and the same error above apeared. Any clues ?

root@Corbin:/home/vador # dpkg --force-overwrite -i /var/cache/apt/archives/xfree86-common_6.8.1-1ubuntu10_all.deb
(Reading database ... 28589 files and directories currently installed.)
Preparing to replace xfree86-common 6.8.1-1ubuntu10 (using .../xfree86-common_6.8.1-1ubuntu10_all.deb) ...
Unpacking replacement xfree86-common ...
Setting up xfree86-common (6.8.1-1ubuntu10) ...
update-rc.d: /etc/init.d/xfree86-common exists during rc.d purge (use -f to force)
dpkg: error processing xfree86-common (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 xfree86-common
root@Corbin:/home/vador #

---

### Post by hardcandy on 2005-01-19
Where you logged into the desktop? You may want to log out to a level 3 console and try the apt-get xfree86 upgrade.

---

