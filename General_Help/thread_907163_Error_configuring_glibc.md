---
title: "Error configuring glibc"
date: 2008-09-01
forum: General Help
---

### Post by JessXe on 2008-09-01
Hello everyone.  I have been following a tutorial about putting together a version of linux to run on my Sega Dreamcast, if you are curious the tutorial can be found [[COLOR="Blue"]_here_[/COLOR]]("http://www.linuxdevices.com/articles/AT7466555948.html").  Anyways I've been making my way through it and when I get to the part about running the config for glibc-2.2.4 with this command:

> CC=sh4-linux-gcc ../glibc-2.2.4/configure \ 
   --host=$TARGET --prefix=$PREFIX \
   --disable-debug --disable-profile \
   --disable-sanity-checks \
   --with-headers=${PREFIX}/${TARGET}/include

I get this output:
> loading cache ./config.cache
checking host system type... sh4-unknown-linux-gnu
checking sysdep dirs... sysdeps/sh/elf sysdeps/unix/sysv/linux/sh/sh4 sysdeps/unix/sysv/linux/sh sysdeps/unix/sysv/linux sysdeps/gnu sysdeps/unix/common sysdeps/unix/mman sysdeps/unix/inet sysdeps/unix/sysv sysdeps/unix/sh sysdeps/unix sysdeps/posix sysdeps/sh/sh4/fpu sysdeps/sh/sh4 sysdeps/sh sysdeps/wordsize-32 sysdeps/ieee754/flt-32 sysdeps/ieee754/dbl-64 sysdeps/ieee754 sysdeps/generic/elf sysdeps/generic
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for pwd... /bin/pwd
checking build system type... sh4-unknown-linux-gnu
checking for gcc... sh4-linux-gcc
checking version of sh4-linux-gcc... v. ?.??, bad
checking for gnumake... no
checking for gmake... no
checking for make... make
checking version of make... 3.81, ok
configure: error:
*** These critical programs are missing or too old:gcc
*** Check the INSTALL file for required versions.

Note: earlier I set TARGET=sh4-linux and PREFIX=/usr/local.

I'm not sure what I'm doing wrong here or what I can do to fix it.  I've seen a few cases with similar problems while searching the internet, but none of those solutions have worked for me.  If it helps to know, I am running Ubuntu Server 8.04.

---

### Post by JessXe on 2008-09-03
bump

---

