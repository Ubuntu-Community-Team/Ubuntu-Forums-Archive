---
title: "Using apt-src (and getting nowhere!)"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by superbiskit on 2009-05-13
I've been trying to pull sources for study and experiment. Under Ubuntu 8.10, I had sporadic success; failures seemed to all be caused by a failure to (properly) decompress the tar files, so that tar complained that the file did not appear to be a proper archive.

Now I am running 9.04.  Now my failure rate is 100%
The following is a typical failed 'apt-src install ...':

W: cannot read /usr/src/debian/changelog
Reading package lists...
Building dependency tree...
Reading state information...
NOTICE: 'dpkg' packaging is maintained in the 'Git' version control system at:
git://git.debian.org/git/dpkg/dpkg.git
Need to get 6864kB of source archives.
'http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.14.24ubuntu1.dsc' dpkg_1.14.24ubuntu1.dsc 1383 MD5Sum:02d12a77aefab211cb0df034979cee1c
'http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.14.24ubuntu1.tar.gz' dpkg_1.14.24ubuntu1.tar.gz 6862200 MD5Sum:1cd858ae505670012cc148c0906a7bf5
E: Did not unpack to /usr/src/dpkg-1.14.24ubuntu1
total 360
-rw-r--r--  1 root src     634 2009-05-12 08:14 apt-src--install_asis-programs_20090512-1214z.log
-rw-r--r--  1 root src    1355 2009-05-12 08:17 apt-src--install_asis-programs_20090512-1217z.log
-rw-r--r--  1 root src     635 2009-05-12 08:18 apt-src--install_dpkg_20090512-1218z.log
-rw-r--r--  1 root root 191359 2008-08-28 01:25 aufs.tar.bz2
-rw-r--r--  1 root root  80936 2008-11-27 17:03 cdfs.tar.bz2
-rw-r--r--  1 root root   6805 2008-05-10 15:47 exmap.tar.gz
drwxr-xr-x  8 root root     77 2009-04-21 21:29 kernel-patches
drwxr-xr-x 22 root root   4096 2009-05-04 12:16 linux-headers-2.6.28-12
drwxr-xr-x  7 root root   4096 2009-05-04 12:24 linux-headers-2.6.28-12-generic
drwxr-xr-x  3 root root   4096 2009-04-20 11:59 nvidia-173.14.16
drwxr-xr-x  7 root root     67 2009-04-20 13:10 rpm


I included the ls -l of the current (/usr/src) directory to show that there is no sign of any of the files supposedly downloaded.

So, Whisky Tango Foxtrot, Interogative

---

