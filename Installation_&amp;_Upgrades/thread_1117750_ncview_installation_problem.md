---
title: "ncview installation problem"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by yajivbs on 2009-04-06
Hi Friends

kindly tell me how to solve. I am installing ncview-1.93d. I am getting        some error kindly help me to solve this problem. 

[root@iccsirws3 ncview-1.93d]# export FC=ifort
[root@iccsirws3 ncview-1.93d]# export CC=icc
[root@iccsirws3 ncview-1.93d]# export NETCDF=/usr/local/netcdf-3.6.3
[root@iccsirws3 ncview-1.93d]# ./configure
checking for gcc... icc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether icc accepts -g... yes
checking for icc option to accept ANSI C... none needed
checking for library containing strerror... none required
checking how to run the C preprocessor... icc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for X... libraries /usr/lib64, headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... no
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking netcdf.h usability... yes
checking netcdf.h presence... yes
checking for netcdf.h... yes
Found netcdf.h in: .
checking for nc_open in -lnetcdf... yes
Found netcdf library file libnetcdf.a in directory .
checking udunits.h usability... yes
checking udunits.h presence... yes
checking for udunits.h... yes
checking for /usr/local/lib/libudunits.a... yes
****************************************************************************
Udunits support enabled.   Note: Udunits did not used to work with MAC OS X
If you are using Mac OS X and have trouble, make sure you are using the
latest udunits package.  If it still doesn't work, remove the udunits library and remake ncview
udunits dirs: include: .  library: /usr/local/lib  libname: udunits
****************************************************************************
checking /usr/local/include/ppm.h usability... no
checking /usr/local/include/ppm.h presence... no
checking for /usr/local/include/ppm.h... no
checking /usr/include/ppm.h usability... no
checking /usr/include/ppm.h presence... no
checking for /usr/include/ppm.h... no
checking /root/include/ppm.h usability... no
checking /root/include/ppm.h presence... no
checking for /root/include/ppm.h... no
checking for ppm_writeppm in -lppm... no
checking for /usr/local/lib/libppm.so... no
checking for /usr/lib/libppm.so... no
checking for /lib/libppm.so... no
checking for /root/lib/libppm.so... no
checking for ppm_writeppm in -lnetpbm... no
checking for /usr/local/lib/libnetpbm.so... no
checking for /usr/lib/libnetpbm.so... no
checking for /lib/libnetpbm.so... no
checking for /root/lib/libnetpbm.so... no
************************************************************************
Note: the -frames option is NOT enabled, because I could not find the 
location of the PPM include file 'ppm.h' or library file
'libppm.a'.  Ncview uses the ppm package to dump out the frames viewed,
which is an easy way to make an mpeg video of the data if you want.
If you do not want this feature, then don't worry about the lack
of ppm support.  If you DO want this, then you must tell me where to find
the ppm package by giving arguments to configure, as follows:
  ./configure -with-ppm_incdir=include_directory -with-ppm_libdir=library_directory
************************************************************************
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
[root@iccsirws3 ncview-1.93d]# make
icc -g -O2  -DINC_UDUNITS   -DNCVIEW_LIB_DIR=\"/usr/local/lib/ncview\" \
                -I.  -I. -I. -c -o ncview.o ncview.c
/usr/include/X11/Xaw/AsciiText.h(83): catastrophic error: could not open source file "X11/Xaw3d/MultiSrc.h"
  #include <X11/Xaw3d/MultiSrc.h>
                                 ^

compilation aborted for ncview.c (code 4)
make: *** [ncview.o] Error 4

Regards
yajivbs

---

