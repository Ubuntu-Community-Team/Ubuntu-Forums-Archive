---
title: "[SOLVED] cupsys update fails repeatedly"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by igeterrors on 2008-12-12
I just managed to upgrade from feisty to gutsy using the alternate cd and everything seems ok except now my update manager is telling me i can install a new version of cupsys, but when I try I get the following error:
```
Preparing to replace cupsys 1.2.8-0ubuntu8.6 (using .../cupsys_1.3.2-1ubuntu7.8_i386.deb) ...
Ignoring nonregistered document cupsys
chown: cannot access `/var/run/cups': No such file or directory
dpkg: error processing /var/cache/apt/archives/cupsys_1.3.2-1ubuntu7.8_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/cupsys_1.3.2-1ubuntu7.8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Any ideas?

---

### Post by Partyboi2 on 2008-12-12
Try making the directory that is missing
```
sudo mkdir /var/run/cups
```
then
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by igeterrors on 2008-12-13
Thanks for the reply. In the interim, I downloaded the cupsys source package, compiled and installed it and it works. I was still getting the update reminder, so then after I saw your reply, I tried:

```
sudo dpkg --configure -a
```
And right away the little update manager icon went from orange to gray. Then I opened the update manager, clicked on "check" and it went through its checking routine and now cupsys doesn't appear in the update window and my system is apparently up to date! :)

Thanks again.

---

