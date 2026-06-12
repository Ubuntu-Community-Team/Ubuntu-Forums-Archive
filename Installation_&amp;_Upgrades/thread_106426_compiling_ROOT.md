---
title: "compiling ROOT"
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by Ana Carolina on 2005-12-20
Hi...

I am trying to install Root 4.04 in my ubuntu 5.10
I am able to do the ./configure
I get
acassis@carolina:~/root/root$ ./configure
Configuring for linux
Checking for libX11 ... /usr/lib
Checking for X11/Xlib.h ... /usr/include
Checking for libXpm ... /usr/lib
Checking whether to build included libfreetype6 ... yes
Checking for GL/gl.h ... no
Checking for libGL, or libMesaGL ... no
Checking for libGLU, or libMesaGLU ... no
Checking for mysql.h ... no
Checking for libmysqlclient_r, libmysqlclient, or mysqlclient ... no
Checking for occi.h ... no
Checking for libclntsh ... no
Checking for libocci ... no
Checking for libpq-fe.h ... no
Checking for libpq ... no
Checking for sql.h ... no
Checking for libsqlod ... no
Checking for rfio_api.h ... no
Checking for libshift, shiftmd, or shift ... no
Checking for libpacklib, packmd, or packlib ... no
Checking for libkernlib, kernmd, or kernlib ... no
Checking for libPythia6 ... no
Checking for libVenus ... no
Checking for dcap.h ... no
Checking for libdcap ... no
Checking for chirp_client.h ... no
Checking for libchirp_client ... no
Checking for AliEnAPI++.h ... no
Checking for libAliEnAPI++ ... no
Checking for jpeglib.h ... no
Checking for png.h ... no
Checking for tiffio.h ... no
Checking for gif_lib.h ... no
Checking for libjpeg ... no
Checking for libtiff ... no
Checking for libz ... no
Checking for libpng ... no
Checking whether to build included libAfterImage ... yes
Checking for ldap.h ... no
Checking for libldap ... no
Checking for Python.h ... no
Checking for libpython2.4, libpython2.3, libpython2.2, python24, python23, or Python ... no
Checking for libxml/tree.h ... no
Checking for libxml2_a, or libxml2 ... no
Checking whether to build xrootd ... yes
Checking for globusdir ... no
Checking for GLOBUS_LOCATION ... no
Checking for libssl ... no
Checking for t_server.h ... no
Checking for libsrp ... no
Checking for libgmp ... no
Checking for libmisc ... no
Checking for pwauth.h ... no
Checking for krb5.h ... no
Checking for libk5crypto ... no
Checking whether we're using MIT Kerberos ... no
Checking for libkrb5 ... no
Checking for kinit ... no
Checking for shadow passwords ... yes
Checking whether to build libTable ... no
Checking for Clarens support ... no
Checking for PEAC support ... no
Checking whether setresuid declared in /usr/include/unistd.h ... no
Creating include ... done
Creating bin ... done
Creating lib ... done
Writing config/Makefile.config ... done
Writing include/config.h ... done
Writing bin/root-config ... done
Writing etc/system.rootrc ... done
Writing etc/system.rootauthrc ... done
Writing etc/system.rootdaemonrc ... done
Writing etc/root.mimes ... done
Writing bin/memprobe ... done
Writing build/misc/root-help.el ... done
Writing macros/html.C ... done
Writing config.status ... done

Enabled support for asimage, builtin_afterimage, builtin_freetype, exceptions, shadowpw, shared, thread, xrootd.

To build the ROOT OpenGL add-on library see README/INSTALL.


To build ROOT type:

   make


But when I try to do the make I got lot's of errors that I don't understand
Does anyone can help me?

acassis@carolina:~/root/root$ make
gcc -O  -pipe -Wall -W -fPIC -Iinclude  -pthread -DINCLUDEDIR=\"/usr/include\" -DOBJSUFFIX=\".o\" -o build/rmkdepend/cppsetup.o -c build/rmkdepend/cppsetup.c
In file included from build/rmkdepend/cppsetup.c:30:
build/rmkdepend/def.h:35:19: error: stdio.h: No such file or directory
build/rmkdepend/def.h:37:20: error: string.h: No such file or directory
build/rmkdepend/def.h:39:19: error: ctype.h: No such file or directory
build/rmkdepend/def.h:40:23: error: sys/types.h: No such file or directory
build/rmkdepend/def.h:41:19: error: fcntl.h: No such file or directory
build/rmkdepend/def.h:42:22: error: sys/stat.h: No such file or directory
build/rmkdepend/def.h:127:20: error: stdlib.h: No such file or directory
build/rmkdepend/cppsetup.c: In function ‘my_if_errors’:
build/rmkdepend/cppsetup.c:149: warning: implicit declaration of function ‘sprintf’
build/rmkdepend/cppsetup.c:149: warning: incompatible implicit declaration of built-in function ‘sprintf’
build/rmkdepend/cppsetup.c:150: warning: implicit declaration of function ‘strlen’
build/rmkdepend/cppsetup.c:150: warning: incompatible implicit declaration of built-in function ‘strlen’
build/rmkdepend/cppsetup.c:151: warning: implicit declaration of function ‘fprintf’
build/rmkdepend/cppsetup.c:151: warning: incompatible implicit declaration of built-in function ‘fprintf’
build/rmkdepend/cppsetup.c:151: error: ‘stderr’ undeclared (first use in this function)
build/rmkdepend/cppsetup.c:151: error: (Each undeclared identifier is reported only once
build/rmkdepend/cppsetup.c:151: error: for each function it appears in.)
build/rmkdepend/cppsetup.c:154: warning: implicit declaration of function ‘putc’
build/rmkdepend/cppsetup.c:160: error: ‘NULL’ undeclared (first use in this function)
build/rmkdepend/cppsetup.c:161: warning: control reaches end of non-void function
build/rmkdepend/cppsetup.c: In function ‘lookup_variable’:
build/rmkdepend/cppsetup.c:178: warning: implicit declaration of function ‘strncpy’
build/rmkdepend/cppsetup.c:178: warning: incompatible implicit declaration of built-in function ‘strncpy’
build/rmkdepend/cppsetup.c:180: error: ‘NULL’ undeclared (first use in this function)
build/rmkdepend/cppsetup.c: In function ‘my_eval_variable’:
build/rmkdepend/cppsetup.c:211: warning: implicit declaration of function ‘isalpha’
build/rmkdepend/cppsetup.c:213: warning: incompatible implicit declaration of built-in function ‘strlen’
build/rmkdepend/cppsetup.c:216: warning: implicit declaration of function ‘strtol’
build/rmkdepend/cppsetup.c:216: error: ‘NULL’ undeclared (first use in this function)
make: *** [build/rmkdepend/cppsetup.o] Error 1


Thanks a lot
Ana

---

### Post by Sutekh on 2005-12-20
Well you could start by installing build-essentials (has make and other tools)
```

sudo apt-get install build-essential

```
Then try ```
./configure
make
sudo checkinstall -D

```
As you were doing before.

---

