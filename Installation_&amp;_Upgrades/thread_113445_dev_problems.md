---
title: "/dev problems"
date: 2006-01-06
forum: Installation &amp; Upgrades
---

### Post by devnu11 on 2006-01-06
I am creating an Ubuntu 5.04 template for OpenVZ and have run into a problem.  There are no /dev/pty, /dev/random, and /dev/urandom devices in /dev.  I have created these devices by the following:

cd /vz/root/111/dev; /vz/root/111/sbin/MAKEDEV pty

This creates the devices just fine.  When I reboot Ubuntu the devices are not there and need to be created all over again.  I have made several templates for other linux distros and once these devices such as /dev/pty are created they are there on reboot.

drwxr-xr-x   4 root root  4096 Jan  1 14:18 dev

How do I solve this problem on Ubuntu? Thanks

---

