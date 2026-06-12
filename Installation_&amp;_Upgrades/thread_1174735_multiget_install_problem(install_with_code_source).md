---
title: "multiget install problem(install with code source)"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by B07030810 on 2009-05-31
I download the code source from [www.sourceforge.net](www.sourceforge.net) and install as the manual .
But it went wrong .This is the tip for install method:
**"Q: How to compile MultiGet from source code (In Linux,FreeBSD,MacOS)?**
    
  A: Refer to the readme_en.txt in source packet. Generally you need wxGTK , wxMac or wxWidgets. The GUI depends  on it. It's very easy to compile wxWidgets:
  
   Download the wxWidgets packets, depend on your system, Linux need wxGTK and Mac need wxMac.  unpack it, enter the directory, make a new directory like static_unicode_build, enter new dir and type in:
  
    ../configure --enable-shared --enable-monolithic --with-gtk=2 --with-libpng=builtin --with-zlib=builtin --with-expat=builtin --with-libtiff=builtin --with-regex=builtin --with-libjpeg=builtin --enable-unicode
  
  if runs ok, then type "make" to compile it. After make finish, type "make install" to install wxWidgets into your system. And then you goto MultiGet source directory , type "make", after a while, you will get the runnable file, MultiGet.
  
  If you change --enable-shared to --disable-shared, then you will get a static MultiGet, it can run without wxWidgets."
When I come to ../configure.......,the terminal shows:configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."
I send a attachment.You can watch it.What's the problem?

---

