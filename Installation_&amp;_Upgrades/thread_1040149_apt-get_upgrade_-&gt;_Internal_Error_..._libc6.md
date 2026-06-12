---
title: "apt-get upgrade -&gt; Internal Error ... libc6"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by kristianrasmussen on 2009-01-15
Hey folks,

I'm having serious problems running

sudo apt-get upgrade and
sudo apt-get dist-upgrade.

I end up with: Internal Error, Could not perform immediate configuration (2) on libc6 from apt-get.

When I'm running sudo apt-get -oDebug::pkgProblemResolver=yes upgrade
I get something like this:
---
Reading package lists... Done
Building dependency tree... Done
Entering ResolveByKeep
[...]
Package perl has broken dep on perl-base
  Keeping Package perl-base due to dep
Package libsasl2-modules has broken dep on libsasl2
  Keeping Package libsasl2 due to dep
Package apt-utils has broken dep on libapt-pkg-libc6.3-6-3.11
  Keeping Package apt due to dep
Package libc6-dev has broken dep on libc6
  Keeping Package libc6 due to dep
Package e2fsprogs has broken dep on e2fslibs
  Keeping Package e2fslibs due to dep
Package php5-mysql has broken dep on phpapi-20051025
  Keeping Package libapache2-mod-php5 due to dep
Package vim has broken dep on vim-runtime
  Keeping Package vim-runtime due to dep
The following packages have been kept back: ...

The [...] represents all of the packages that don't report errors. I've tried to google this problem and found some answers that pointed to 
sudo apt-get install libc6 
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils findutils libc6-dev libc6-i686 linux-libc-dev
Suggested packages:
  binutils-doc mlocate glibc-doc manpages-dev
The following packages will be REMOVED:
  linux-kernel-headers
The following NEW packages will be installed:
  linux-libc-dev
The following packages will be upgraded:
  binutils findutils libc6 libc6-dev libc6-i686
5 upgraded, 1 newly installed, 1 to remove and 233 not upgraded.
Need to get 0B/11,7MB of archives.
After unpacking 2580kB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, Could not perform immediate configuration (2) on libc6

Now i've tried updating apt-get and aptitude, no luck. They just break with a wrong reference to GLIBC. As of now I can use apt-get without any worries. But how to fix these broken dependencies?


I seriously hope you smart people got an answer :-)

Best regards

Kristian

---

### Post by atulgoyal52 on 2009-03-31
Were you able to solve this problem. Since I also got the same problem.

---

