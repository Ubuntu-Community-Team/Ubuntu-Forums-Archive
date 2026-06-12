---
title: "Problems with video card in Ubuntu"
date: 2009-04-26
forum: Hardware
---

### Post by ahcvandinter on 2009-04-26
Hello,

I have installed Jaunty Jackalope on my laptop and until now I am very satisfied with it. There is one problem that bothers me though and that is that I am unable to use Compiz. After using Google I have read that I have to install the right drivers. Using the command line I have  found the following details:

antoine@antoine-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
antoine@antoine-laptop:~$ X -version

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux antoine-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
antoine@antoine-laptop:~$ gcc -v
Ingebouwde specs worden gebruikt.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc versie 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 
antoine@antoine-laptop:~$ 

Can somebody please help me. I would really like to use Compiz.

---

