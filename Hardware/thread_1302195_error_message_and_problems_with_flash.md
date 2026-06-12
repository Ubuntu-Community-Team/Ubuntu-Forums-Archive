---
title: "error message and problems with flash"
date: 2009-10-26
forum: Hardware
---

### Post by ricethins on 2009-10-26
While trying to get flash to work in my AMD64 with Ubuntu 9.4 I cannot get the flash installed and there are problems with other updates or upgrades as well.
This is a message I got while trying to trouble shoot the issue:
(I'll also post some screenshots of other related error messages)

Reading package lists... Done
root@manuel-HPlaptop:/home/manuel# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.27-11-generic (2.6.27-11.31) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.27-11-generic)
dpkg: error processing linux-image-2.6.27-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.27-9-generic (2.6.27-9.19) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.27-9-generic)
dpkg: error processing linux-image-2.6.27-9-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.28-11-generic (2.6.28-11.42) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.28-11-generic)
dpkg: error processing linux-image-2.6.28-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-11-generic:
 linux-restricted-modules-2.6.28-11-generic depends on linux-image-2.6.28-11-generic; however:
  Package linux-image-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-11-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.27-11-generic
 linux-image-2.6.27-9-generic
 linux-image-2.6.28-11-generic
 linux-restricted-modules-2.6.28-11-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@manuel-HPlaptop:/home/manuel# check
bash: check: command not found
root@manuel-HPlaptop:/home/manuel# apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
root@manuel-HPlaptop:/home/manuel# apt-get check

---

### Post by ricethins on 2009-10-26
I'll try to post some screenshots as well....

---

### Post by ricethins on 2009-10-26
I will be most grateful for any help in getting my system sorted out.

---

