---
title: "iMON VFD compling problem"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by andrewsawyer on 2006-02-03
Hiya,

I'm trying to install LCDproc 0.4.5 for iMON per [http://venky.ws/projects/imon/#lcdproc](http://venky.ws/projects/imon/#lcdproc) howeer I'm having troubles.  I have follwoed step by step however get errorrs when doing 'make'.

I have copied the terminal screen from start to finish after the tarball was extracted.  If someone could see where it was going wrong, it'd be much appreciated as I don't have a clue where to start!  For what it's worth, I think that ./configure went ok!

```
root@mediacentre:/home/mythtv/Desktop/lcdproc-0.4.5-imon# aclocal; autoheader; autoconf; automake -a
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader:
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows to define a template without
autoheader: WARNING: `acconfig.h':
autoheader:
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader:
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
root@mediacentre:/home/mythtv/Desktop/lcdproc-0.4.5-imon# ./configure checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether to enable debugging... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for gethostbyname... yes
checking for connect... yes
checking for inet_aton... yes
checking for kstat_open in -lkstat... no
checking for nanosleep in -lposix4... no
checking for getloadavg... yes
checking for swapctl... no
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking procfs.h usability... no
checking procfs.h presence... no
checking for procfs.h... no
checking sys/procfs.h usability... yes
checking sys/procfs.h presence... yes
checking for sys/procfs.h... yes
checking sys/loadavg.h usability... no
checking sys/loadavg.h presence... no
checking for sys/loadavg.h... no
checking utmpx.h usability... yes
checking utmpx.h presence... yes
checking for utmpx.h... yes
checking for kvm_open in -lkvm... no
checking for kvm_open in -lkvm with -lelf... no
checking sched.h usability... yes
checking sched.h presence... yes
checking for sched.h... yes
checking sys/sched.h usability... no
checking sys/sched.h presence... no
checking for sys/sched.h... no
checking machine/cpufunc.h usability... no
checking machine/cpufunc.h presence... no
checking for machine/cpufunc.h... no
checking for sys/types.h... (cached) yes
checking machine/pio.h usability... no
checking machine/pio.h presence... no
checking for machine/pio.h... no
checking machine/sysarch.h usability... no
checking machine/sysarch.h presence... no
checking for machine/sysarch.h... no
checking sys/cpuvar.h usability... no
checking sys/cpuvar.h presence... no
checking for sys/cpuvar.h... no
checking for System V IPC headers... yes
checking for union semun... no
checking for sched_setscheduler... yes
checking for sched_setscheduler in -lposix4... no
checking for sched_setscheduler in -lposix4... (cached) no
checking for sched_setscheduler in -lrt... yes
checking for sched_setscheduler in -lrt... (cached) yes
checking for i386_get_ioperm in -li386... no
checking for i386_get_ioperm in -li386... (cached) no
checking for i386_get_ioperm in -lc... no
checking for i386_get_ioperm in -lc... (cached) no
checking for ioperm... yes
checking sys/io.h usability... yes
checking sys/io.h presence... yes
checking for sys/io.h... yes
checking sys/perm.h usability... yes
checking sys/perm.h presence... yes
checking for sys/perm.h... yes
checking for unistd.h... (cached) yes
checking for a parallel port... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking kvm.h usability... no
checking kvm.h presence... no
checking for kvm.h... no
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/sysctl.h usability... yes
checking sys/sysctl.h presence... yes
checking for sys/sysctl.h... yes
checking sys/dkstat.h usability... no
checking sys/dkstat.h presence... no
checking for sys/dkstat.h... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for uid_t in sys/types.h... yes
checking whether gcc needs -traditional... no
checking return type of signal handlers... void
checking for select... yes
checking for socket... yes
checking for strdup... yes
checking for strerror... yes
checking for strtol... yes
checking for uname... yes
checking for cfmakeraw... yes
checking for your mounted filesystem table... /etc/mtab
checking for fcntl.h... (cached) yes
checking sys/dustat.h usability... no
checking sys/dustat.h presence... no
checking for sys/dustat.h... no
checking for sys/param.h... (cached) yes
checking sys/statfs.h usability... yes
checking sys/statfs.h presence... yes
checking for sys/statfs.h... yes
checking sys/fstyp.h usability... no
checking sys/fstyp.h presence... no
checking for sys/fstyp.h... no
checking mnttab.h usability... no
checking mnttab.h presence... no
checking for mnttab.h... no
checking mntent.h usability... yes
checking mntent.h presence... yes
checking for mntent.h... yes
checking utime.h usability... yes
checking utime.h presence... yes
checking for utime.h... yes
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking sys/vfs.h usability... yes
checking sys/vfs.h presence... yes
checking for sys/vfs.h... yes
checking sys/mount.h usability... yes
checking sys/mount.h presence... yes
checking for sys/mount.h... yes
checking sys/filsys.h usability... no
checking sys/filsys.h presence... no
checking for sys/filsys.h... no
checking sys/fs_types.h usability... no
checking sys/fs_types.h presence... no
checking for sys/fs_types.h... no
checking for getmntinfo... no
configure: checking how to get filesystem space usage...
checking for statvfs... yes
configure: checking for which drivers to compile...
checking ncurses.h usability... no
checking ncurses.h presence... no
checking for ncurses.h... no
checking curses.h usability... no
checking curses.h presence... no
checking for curses.h... no
checking for main in -lncurses... no
checking for main in -lcurses... no
configure: WARNING: The curses driver needs the curses (or ncurses) library.
checking for acs_map in curses.h... no
checking for _acs_char in curses.h... no
checking for redrawwin() in curses... no
checking for wcolor_set() in curses... no
Will compile drivers: lcdm001,mtxorb,cfontz,cwlnx,text,lb216,bayrad,glk,sgx120,imon
configure: creating ./config.status
config.status: creating Makefile
config.status: creating shared/Makefile
config.status: creating server/Makefile
config.status: creating server/drivers/Makefile
config.status: creating clients/Makefile
config.status: creating clients/lcdproc/Makefile
config.status: creating clients/examples/Makefile
config.status: creating clients/headlines/Makefile
config.status: creating clients/metar/Makefile
config.status: creating docs/Makefile
config.status: creating docs/lcdproc-user/Makefile
config.status: creating docs/lcdproc-user/drivers/Makefile
config.status: creating scripts/Makefile
config.status: creating scripts/init-LCDd.debian
config.status: creating scripts/init-LCDd.rpm
config.status: creating scripts/init-lcdproc.debian
config.status: creating scripts/init-lcdproc.rpm
config.status: creating LCDproc.list
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
root@mediacentre:/home/mythtv/Desktop/lcdproc-0.4.5-imon# make cd . && autoheader
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader:
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows to define a template without
autoheader: WARNING: `acconfig.h':
autoheader:
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader:
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
make  all-recursive
make[1]: Entering directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon'
Making all in shared
make[2]: Entering directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/shared'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/shared'
Making all in clients
make[2]: Entering directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/clients'
Making all in examples
make[3]: Entering directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/clients/examples'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/clients/examples'
Making all in headlines
make[3]: Entering directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/clients/headlines'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/clients/headlines'
Making all in lcdproc
make[3]: Entering directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/clients/lcdproc'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/clients/lcdproc'
Making all in metar
make[3]: Entering directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/clients/metar'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/clients/metar'
make[3]: Entering directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/clients'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/clients'
make[2]: Leaving directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/clients'
Making all in server
make[2]: Entering directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/server'
Making all in drivers
make[3]: Entering directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/server/drivers'
gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I./.. -I../..    -Wall -O3 -c lb216.c
lb216.c:32:21: error: curses.h: No such file or directory
lb216.c: In function &#8216;LB216_init&#8217;:
lb216.c:191: warning: pointer targets in assignment differ in signedness
make[3]: *** [lb216.o] Error 1
make[3]: Leaving directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/server/drivers'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon/server'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mythtv/Desktop/lcdproc-0.4.5-imon'
make: *** [all-recursive-am] Error 2
root@mediacentre:/home/mythtv/Desktop/lcdproc-0.4.5-imon#

```

Many thanks,

Andy

---

### Post by eleybourn on 2006-07-22
I had that same problem. You need to install libncurses5-dev.

Best of luck

---

