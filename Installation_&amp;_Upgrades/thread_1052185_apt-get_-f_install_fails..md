---
title: "apt-get -f install fails."
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by kscarz on 2009-01-27
I could use some help with fixing the following problem. I attempted to perform an apt-get dist-upgrade and then started getting errors with xfont and to fix my dependencies..

Any help is greatly appreciated.


apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  xutils xutils-dev
Suggested packages:
  pdksh
The following NEW packages will be installed:
  xutils xutils-dev
0 upgraded, 2 newly installed, 0 to remove and 158 not upgraded.
3 not fully installed or removed.
Need to get 0B/367kB of archives.
After unpacking 1966kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 51723 files and directories currently installed.)
Unpacking xutils-dev (from .../xutils-dev_1%3a7.1.ds-6_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xutils-dev_1%3a7.1.ds-6_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/imake.1.gz', which is also in package imake
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking xutils (from .../xutils_1%3a7.1.ds.3-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xutils_1%3a7.1.ds.3-1_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/showrgb.1.gz', which is also in package xrgb
Errors were encountered while processing:
 /var/cache/apt/archives/xutils-dev_1%3a7.1.ds-6_i386.deb
 /var/cache/apt/archives/xutils_1%3a7.1.ds.3-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kscarz on 2009-02-01
Just in case this helps I was able to correct this by using the command dpkg --install --force-all packagename for each error that the dependencies complained about. Doing an apt-get dist-ugrade caused the error.. 

Cheers

---

