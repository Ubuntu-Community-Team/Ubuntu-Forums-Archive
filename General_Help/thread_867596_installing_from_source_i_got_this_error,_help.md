---
title: "installing from source i got this error, help?"
date: 2008-07-23
forum: General Help
---

### Post by chris4585 on 2008-07-23
I'm trying to install scrot on SliTaz, and I get this error:

```
chris4585@slitaz:~$ cd scrot-0.8/
chris4585@slitaz:~/scrot-0.8$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
chris4585@slitaz:~/scrot-0.8$ 
```

any help? thanks in advance

this is my configure.log

```

configure:1847: $? = 0
configure:1849: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-pc-linux-gnu
Configured with: ../gcc-4.2.3/configure --prefix=/usr --libexecdir=/usr/lib --infodir=/usr/share/info --mandir=/usr/share/man --enable-nls --enable-languages=c,c++ --enable-shared --with-system-zlib --enable-clocale=gnu --enable-objc-gc --enable-__cxa_atexit --enable-threads=posix --with-tune=i486 i486-pc-linux-gnu
Thread model: posix
gcc version 4.2.3
configure:1852: $? = 0
configure:1854: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:1857: $? = 1
configure:1881: checking for C compiler default output
configure:1884: gcc    conftest.c  >&5
gcc: error trying to exec 'as': execvp: No such file or directory
configure:1887: $? = 1
configure: failed program was:
| #line 1861 "configure"
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "scrot"
| #define VERSION "0.8"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:1925: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CC_set=''
ac_cv_env_CC_value=''
ac_cv_env_CFLAGS_set=''
ac_cv_env_CFLAGS_value=''
ac_cv_env_CPPFLAGS_set=''
ac_cv_env_CPPFLAGS_value=''
ac_cv_env_LDFLAGS_set=''
ac_cv_env_LDFLAGS_value=''
ac_cv_env_build_alias_set=''
ac_cv_env_build_alias_value=''
ac_cv_env_host_alias_set=''
ac_cv_env_host_alias_value=''
ac_cv_env_target_alias_set=''
ac_cv_env_target_alias_value=''
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_ac_ct_CC='gcc'
ac_cv_prog_make_make_set='yes'

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='/home/chris4585/scrot-0.8/missing aclocal-1.4'
AUTOCONF='/home/chris4585/scrot-0.8/missing autoconf'
AUTOHEADER='/home/chris4585/scrot-0.8/missing autoheader'
AUTOMAKE='/home/chris4585/scrot-0.8/missing automake-1.4'
CC='gcc'
CFLAGS=''
CPPFLAGS=''
DEFS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EXEEXT=''
GIBLIB_CFLAGS=''
GIBLIB_CONFIG=''
GIBLIB_LIBS=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
LDFLAGS=''
LIBOBJS=''
LIBOBJS=''
LIBS=''
LTLIBOBJS=''
MAINT=''
MAINTAINER_MODE_FALSE=''
MAINTAINER_MODE_TRUE=''
MAKEINFO='/home/chris4585/scrot-0.8/missing makeinfo'
OBJEXT=''
PACKAGE='scrot'
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
SET_MAKE=''
SHELL='/bin/sh'
VERSION='0.8'
ac_ct_CC='gcc'
bindir='${exec_prefix}/bin'
build_alias=''
datadir='${prefix}/share'
exec_prefix='NONE'
host_alias=''
includedir='${prefix}/include'
infodir='${prefix}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
oldincludedir='/usr/include'
prefix='NONE'
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE "scrot"
#define PACKAGE_BUGREPORT ""
#define PACKAGE_NAME ""
#define PACKAGE_STRING ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define VERSION "0.8"

configure: exit 77

```

---

### Post by jimv on 2008-07-23
You need to install some additional packages.  Here's the terminal command:

```
sudo apt-get install install build-essential automake
```

---

### Post by chris4585 on 2008-07-25
> **jimv said:**
> You need to install some additional packages.  Here's the terminal command:

```
sudo apt-get install install build-essential automake
```

sorry, I'm not on Ubuntu, I'm on SliTaz, I can't install build-essential from the SliTaz repo, I should ask on the SliTaz forums, reason why I didn't was I didnt want to bother signing up when I can already get help on the Ubuntu Forums.

Thanks for the help though

---

### Post by thatsmyboy on 2011-09-29
From Wikipedia:

> The GNU build system comprises the GNU utility programs Autoconf, Automake, and Libtool.

These three are essential for what you need. you can find them in the Slitaz Packages Manager. Also look out for coreutils, and glibc .

Just solved this problem myself btw.

---

