---
title: "Optimisations for core duo with apt-build"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by angrycore on 2007-05-29
Hi. I have a laptop with core duo inside, running kubuntu feisty and a fixed idea to optimize the OS as much as I can. I've already compiled a custom kernel from linux.org with patches from [www.linuxpowertop.org](www.linuxpowertop.org), support of suspend2 and several hardware optimizations. Now I want to recompile several performance-essential system packages using apt-build to improve start-up time and optimize the whole system performance a bit.
After configuring apt-build I've tried to recompile some KDE packages and noticed that while apt-build runs configure script for the package It treats my system as i486-linux-gnu. It happens only using apt-build - when I compile anything by hands it is ok - i686-pc-linux-gnu, also it is ok if I use dpkg-buildpackage. 

So the question is how can I tell apt-build to use i686-pc-linux-gnu?)

Here is my /etc/apt/apt-build.conf
```
build-dir = /var/cache/apt-build/build
repository-dir = /var/cache/apt-build/repository
Olevel = -O2
mtune = -mtune=prescott
options = "-pipe -fomit-frame-pointer"
make_options = "-j2"

```
Here are several build-essential environment variables:
```

vlok@core-laptop:~$ echo $CHOST
i686-pc-linux-gnu
vlok@core-laptop:~$ echo $HOSTTYPE
i686
vlok@core-laptop:~$ echo $CFLAGS
-march=prescott -O2 -pipe -fomit-frame-pointer
vlok@core-laptop:~$ echo $CXXFLAGS
-march=prescott -O2 -pipe -fomit-frame-pointer

```

---

### Post by Ken_Lewis81 on 2007-05-30
I don't think 'prescott' will give you the best juice for your programs. Perhaps you should use -march=i686 and -mcpu=pentium-m instead, because that's the family history of the Core series of chips and will be able to use the best optimisations should they be available.  make_options should be '-j3' to get the best from your dual cpu cores, the rule being that 'j' gives you parallel jobs, and needs to be set as 1+ No. of CPUs.

Take care.
Ken.

---

### Post by angrycore on 2007-05-30
Hmm.. according to gentoo-wiki prescott is the correct microarchitecture to use with Core Solo/Duo:
[http://gentoo-wiki.com/Safe_Cflags#Intel_Core_Solo.2FDuo](http://gentoo-wiki.com/Safe_Cflags#Intel_Core_Solo.2FDuo)
Thanks for '-j3' option)
Recently I've found out that dpkg-buildpackage uses i486-linux-gnu too) So I've missed a bit in my previous post)
It seems i486-linux-gnu is caused by dpkg-architecture. Here is it's output:
```
vlok@core-laptop:~$ dpkg-architecture
DEB_BUILD_ARCH=i386
DEB_BUILD_ARCH_OS=linux
DEB_BUILD_ARCH_CPU=i386
DEB_BUILD_GNU_CPU=i486
DEB_BUILD_GNU_SYSTEM=linux-gnu
DEB_BUILD_GNU_TYPE=i486-linux-gnu
DEB_HOST_ARCH=i386
DEB_HOST_ARCH_OS=linux
DEB_HOST_ARCH_CPU=i386
DEB_HOST_GNU_CPU=i486
DEB_HOST_GNU_SYSTEM=linux-gnu
DEB_HOST_GNU_TYPE=i486-linux-gnu

```
How can I change its values? :) If I try:
```
vlok@core-laptop:~$ sudo dpkg-architecture -ai686 -ti686-pc-linux-gnu -f
dpkg-architecture: warning: Default GNU system type  for Debian arch i686 does not match specified GNU system type i686-pc-linux-gnu
dpkg-architecture: warning: Specified GNU system type i686-pc-linux-gnu does not match gcc system type i486-linux-gnu.
DEB_BUILD_ARCH=i386
DEB_BUILD_ARCH_OS=linux
DEB_BUILD_ARCH_CPU=i386
DEB_BUILD_GNU_CPU=i486
DEB_BUILD_GNU_SYSTEM=linux-gnu
DEB_BUILD_GNU_TYPE=i486-linux-gnu
DEB_HOST_ARCH=i686
DEB_HOST_ARCH_OS=linux
DEB_HOST_ARCH_CPU=i686
DEB_HOST_GNU_CPU=i686
DEB_HOST_GNU_SYSTEM=pc-linux-gnu
DEB_HOST_GNU_TYPE=i686-pc-linux-gnu

```
And nothing changes after it. Maybe that's because gcc has i486-linux-gnu as target:
```
vlok@core-laptop:~$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

```
But how can I change it?

---

### Post by Ken_Lewis81 on 2007-06-05
I'd hope there's directions in "[man dpkg-architecture](http://huygens.ca.infn.it/cgi-bin/man/man2html?1+dpkg-architecture)" to help.  It seems that you'd be best off putting the terms before the build:
```
DEB_BUILD_ARCH_CPU=i686 DEB_BUILD_GNU_TYPE=i686-linux-gnu fakeroot apt-build *blah blah blah*
```

Hope this helps
Take care.
Ken.

---

