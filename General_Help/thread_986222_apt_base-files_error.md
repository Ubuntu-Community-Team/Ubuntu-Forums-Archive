---
title: "apt base-files error"
date: 2008-11-18
forum: General Help
---

### Post by njparton on 2008-11-18
Can someone tell me how to fix the problem below please.  It's driving me up the wall.  I've updated apt several times but it's driving me nuts.  I can't seem to remove the offending base-files package from dpkg to try again.

neil@nas:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libisccc30 libisccfg30 linux-image-server linux-server openssh-client openssh-server
The following packages will be upgraded:
  clamav clamav-base clamav-freshclam dbus dbus-x11 firefox firefox-3.0 firefox-3.0-gnome-support libclamav3 libdbus-1-3 libmysqlclient15off
  libpam-smbpass libsmbclient module-init-tools mysql-client mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 passwd samba
  samba-common samba-doc smbclient smbfs winbind xulrunner-1.9 xulrunner-1.9-gnome-support
28 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
Need to get 0B/88.0MB of archives.
After this operation, 795kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Setting up base-files (4.0.1ubuntu5.8.04.3) ...
chown: invalid group: `root:utmp'
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by njparton on 2008-11-20
Solved via the following bug if anyone else comes across this thread:

[https://bugs.launchpad.net/ubuntu/+source/base-files/+bug/292116](https://bugs.launchpad.net/ubuntu/+source/base-files/+bug/292116)

---

