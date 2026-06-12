---
title: "no include(stdio.h, ...) files after installed 8.04.1"
date: 2008-07-17
forum: General Help
---

### Post by mjinli2008 on 2008-07-17
I installed ubuntu 8.04.1 by usig of wubi, but there are no include files:


xyz@xyz-desktop:/usr/include$ ls -FC
compiz/  cups/  dbus-1.0/  evince-2.20/  gpilotd/  libgpilotdCM/  python2.4/  python2.5/  X11/
xyz@xyz-desktop:/usr/include$
xyz@xyz-desktop:/usr/include$ uname -a
Linux xyz-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
/etc$ cat lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

How do I get the include files ?
What else I am missing ?

Thanks and regards.
mli

---

### Post by ago on 2008-07-17
Wubi installs the same version of the packages as in a normal installation. You might want to install *-dev packages

For instance /usr/include/stdio.h is provided by libc6-dev

---

### Post by mjinli2008 on 2008-07-21
Hi,
Thank you very much.
You solved my problem.

May I suggest that after installation the minimum packages, automatically install
the dev packages from Wubi?

The reason is that I have to setup the wireless driver, I downloaded
ndiswrapper-1.53, when I try to compile it, I got 
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory

People might have this or that problem, they search the internet, and download
the software, some needs to be compiled at the box.

Anyway, thank you very much again.

Thanks and regards.
mli

------------------my install log(begin)---------------
root@mli-desktop:/home/mli/archieve#  modprobe loop
root@mli-desktop:/home/mli/archieve#  mount -t iso9660 -o loop  ubuntu-8.04.1-desktop-i386.iso /media/cdrom

root@mli-desktop:~# apt-get install libc6-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  linux-libc-dev
Suggested packages:
  glibc-doc manpages-dev
The following NEW packages will be installed:
  libc6-dev linux-libc-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 696kB/4039kB of archives.
After this operation, 17.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-libc-dev 2.6.24-19.36 [696kB]
Media change: please insert the disc labeled
 'Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled                                                    
 'Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)'
in the drive '/cdrom/' and press enter

Fetched 696kB in 18min22s (631B/s)                                                              
Selecting previously deselected package linux-libc-dev.
(Reading database ... 96127 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-19.36_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_i386.deb) ...
Setting up linux-libc-dev (2.6.24-19.36) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
root@mli-desktop:~#


root@mli-desktop:/usr/include# ls
aio.h        envz.h          ieee754.h     netdb.h     rpc          termio.h

------------------my install log(end)---------------

---

