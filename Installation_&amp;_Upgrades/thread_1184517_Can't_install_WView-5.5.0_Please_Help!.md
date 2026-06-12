---
title: "Can't install WView-5.5.0 Please Help!"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by NDBrinkley on 2009-06-11
Hi, Sorry if I come across as a complete idiot but I am quite new to Linux. I absolutely love it and am trying really hard to cut all ties with Microsoft ;). I am doing well in finding Linux alternatives to MS software, however, I have a Davis VP2 Weather Station and want to install WView as an alternative to WeatherLink for Windows. My problem is that, while installing software in .deb format is easy, I am really struggling with compiling software from source.

I am really keen to learn Linux and any help would be greatly appreciated (in layman's term please). Thank you. 

Here goes,
I have downloaded WView-5.5.0, 'unzipped' it and placed the files in my home dir (/ndbrinkley).
I am aware that there is a list of dependences but I am unsure as to the easiest way to install them (apt-get install does not seem to be able to find them + Synaptic give me a number of files and I am unsure which are the correct ones). 
Using the terminal I cd to the folder wview-5.5.0 and enter ./configure

**I get:**
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking whether byte ordering is bigendian... no
checking whether struct tm is in sys/time.h or time.h... time.h
checking for struct tm.tm_zone... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for strncpy in -lc... yes
checking for gdImageCreate in -lgd... no
checking for exp in -lm... yes
checking for png_write_chunk in -lpng... no
checking for sqlite3_open in -lsqlite3... no
checking for radSystemGetUpTimeMS in -lrad... no
checking for inflate in -lz... no
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for pid_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... (cached) time.h
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for sys/time.h... (cached) yes
checking for unistd.h... (cached) yes
checking for alarm... yes
checking for working mktime... yes
checking return type of signal handlers... void
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for localtime_r... yes
checking for memset... yes
checking for mkdir... yes
checking for pow... yes
checking for strrchr... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating stations/Makefile
config.status: creating stations/Simulator/Makefile
config.status: creating stations/VantagePro/Makefile
config.status: creating stations/VantagePro/vpconfig/Makefile
config.status: creating stations/WS-2300/Makefile
config.status: creating stations/WMR918/Makefile
config.status: creating stations/WXT510/Makefile
config.status: creating stations/WXT510/wxt510config/Makefile
config.status: creating htmlgenerator/Makefile
config.status: creating alarms/Makefile
config.status: creating cwop/Makefile
config.status: creating http/Makefile
config.status: creating ftp/Makefile
config.status: creating ssh/Makefile
config.status: creating procmon/Makefile
config.status: creating wviewconfig/Makefile
config.status: creating wviewmgmt/Makefile
config.status: creating dbexport/Makefile
config.status: creating examples/Makefile
config.status: creating examples/Debian/Makefile
config.status: creating examples/FedoraCore/Makefile
config.status: creating examples/FreeBSD/Makefile
config.status: creating examples/MacOSX/wview/Makefile
config.status: creating examples/NSLU2/Makefile
config.status: creating examples/SuSE/Makefile
config.status: creating utilities/Makefile
config.status: creating utilities/wlk2sqlite/Makefile
config.status: creating utilities/sqlite2wlk/Makefile
config.status: creating utilities/archive-be2le/Makefile
config.status: creating utilities/archive-le2be/Makefile
config.status: creating utilities/hilowcreate/Makefile
config.status: creating config.h
config.status: executing depfiles commands

Next, I enter:
make

**I get:**
make  all-recursive
make[1]: Entering directory `/home/ndbrinkley/wview-5.5.0'
Making all in stations
make[2]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations'
Making all in Simulator
make[3]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/Simulator'
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT sensor.o -MD -MP -MF .deps/sensor.Tpo -c -o sensor.o `test -f '../../common/sensor.c' || echo './'`../../common/sensor.c
../../common/sensor.c:26:23: error: radmsgLog.h: No such file or directory
In file included from ../../common/sensor.c:30:
../../common/sensor.h:39:21: error: radlist.h: No such file or directory
../../common/sensor.h:40:24: error: radbuffers.h: No such file or directory
In file included from ../../common/sensor.h:42,
                 from ../../common/sensor.c:30:
../../common/sysdefs.h:35:24: error: radsysdefs.h: No such file or directory
In file included from ../../common/sensor.h:42,
                 from ../../common/sensor.c:30:
../../common/sysdefs.h:200: error: expected ‘)’ before ‘daemonBitMask’
../../common/sysdefs.h:264: error: expected ‘)’ before ‘packedDate’
../../common/sysdefs.h:271: error: expected ‘)’ before ‘newDate’
../../common/sysdefs.h:278: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘wvutilsIncrementPackedTime’
In file included from ../../common/sensor.h:43,
                 from ../../common/sensor.c:30:
../../common/datadefs.h:229: error: expected specifier-qualifier-list before ‘USHORT’
In file included from ../../common/sensor.c:30:
../../common/sensor.h:61: error: expected specifier-qualifier-list before ‘NODE’
../../common/sensor.h:68: error: expected specifier-qualifier-list before ‘RADLIST’
../../common/sensor.c: In function ‘sensorGetLowTime’:
../../common/sensor.c:193: error: ‘PRI_MEDIUM’ undeclared (first use in this function)
../../common/sensor.c:193: error: (Each undeclared identifier is reported only once
../../common/sensor.c:193: error: for each function it appears in.)
../../common/sensor.c: In function ‘sensorGetLowDate’:
../../common/sensor.c:224: error: ‘PRI_MEDIUM’ undeclared (first use in this function)
../../common/sensor.c: In function ‘sensorGetHighTime’:
../../common/sensor.c:264: error: ‘PRI_MEDIUM’ undeclared (first use in this function)
../../common/sensor.c: In function ‘sensorGetHighDate’:
../../common/sensor.c:295: error: ‘PRI_MEDIUM’ undeclared (first use in this function)
../../common/sensor.c: In function ‘AgeAccumulator’:
../../common/sensor.c:459: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c:461: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c:463: error: ‘struct <anonymous>’ has no member named ‘secondsInAccumulator’
../../common/sensor.c:463: error: ‘WV_ACCUM_SAMPLE’ has no member named ‘sampleTime’
../../common/sensor.c:466: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c: In function ‘sensorAccumInit’:
../../common/sensor.c:486: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c:487: error: ‘struct <anonymous>’ has no member named ‘secondsInAccumulator’
../../common/sensor.c:488: error: ‘struct <anonymous>’ has no member named ‘sum’
../../common/sensor.c: In function ‘sensorAccumExit’:
../../common/sensor.c:496: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c:498: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c: In function ‘sensorAccumAddSample’:
../../common/sensor.c:515: error: ‘WV_ACCUM_SAMPLE’ has no member named ‘value’
../../common/sensor.c:516: error: ‘WV_ACCUM_SAMPLE’ has no member named ‘sampleTime’
../../common/sensor.c:517: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c:517: error: ‘NODE_PTR’ undeclared (first use in this function)
../../common/sensor.c:517: error: expected ‘)’ before ‘newNode’
../../common/sensor.c: In function ‘sensorAccumGetTotal’:
../../common/sensor.c:531: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c:533: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c:533: error: ‘NODE_PTR’ undeclared (first use in this function)
../../common/sensor.c:533: error: expected ‘)’ before ‘nodePtr’
../../common/sensor.c:535: error: ‘WV_ACCUM_SAMPLE’ has no member named ‘value’
../../common/sensor.c: In function ‘sensorAccumGetAverage’:
../../common/sensor.c:546: error: ‘struct <anonymous>’ has no member named ‘samples’
make[3]: *** [sensor.o] Error 1
make[3]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/Simulator'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ndbrinkley/wview-5.5.0'
make: *** [all] Error 2

Then:
make install

**I get:**
Making install in stations
make[1]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations'
Making install in Simulator
make[2]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/Simulator'
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT sensor.o -MD -MP -MF .deps/sensor.Tpo -c -o sensor.o `test -f '../../common/sensor.c' || echo './'`../../common/sensor.c
../../common/sensor.c:26:23: error: radmsgLog.h: No such file or directory
In file included from ../../common/sensor.c:30:
../../common/sensor.h:39:21: error: radlist.h: No such file or directory
../../common/sensor.h:40:24: error: radbuffers.h: No such file or directory
In file included from ../../common/sensor.h:42,
                 from ../../common/sensor.c:30:
../../common/sysdefs.h:35:24: error: radsysdefs.h: No such file or directory
In file included from ../../common/sensor.h:42,
                 from ../../common/sensor.c:30:
../../common/sysdefs.h:200: error: expected ‘)’ before ‘daemonBitMask’
../../common/sysdefs.h:264: error: expected ‘)’ before ‘packedDate’
../../common/sysdefs.h:271: error: expected ‘)’ before ‘newDate’
../../common/sysdefs.h:278: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘wvutilsIncrementPackedTime’
In file included from ../../common/sensor.h:43,
                 from ../../common/sensor.c:30:
../../common/datadefs.h:229: error: expected specifier-qualifier-list before ‘USHORT’
In file included from ../../common/sensor.c:30:
../../common/sensor.h:61: error: expected specifier-qualifier-list before ‘NODE’
../../common/sensor.h:68: error: expected specifier-qualifier-list before ‘RADLIST’
../../common/sensor.c: In function ‘sensorGetLowTime’:
../../common/sensor.c:193: error: ‘PRI_MEDIUM’ undeclared (first use in this function)
../../common/sensor.c:193: error: (Each undeclared identifier is reported only once
../../common/sensor.c:193: error: for each function it appears in.)
../../common/sensor.c: In function ‘sensorGetLowDate’:
../../common/sensor.c:224: error: ‘PRI_MEDIUM’ undeclared (first use in this function)
../../common/sensor.c: In function ‘sensorGetHighTime’:
../../common/sensor.c:264: error: ‘PRI_MEDIUM’ undeclared (first use in this function)
../../common/sensor.c: In function ‘sensorGetHighDate’:
../../common/sensor.c:295: error: ‘PRI_MEDIUM’ undeclared (first use in this function)
../../common/sensor.c: In function ‘AgeAccumulator’:
../../common/sensor.c:459: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c:461: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c:463: error: ‘struct <anonymous>’ has no member named ‘secondsInAccumulator’
../../common/sensor.c:463: error: ‘WV_ACCUM_SAMPLE’ has no member named ‘sampleTime’
../../common/sensor.c:466: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c: In function ‘sensorAccumInit’:
../../common/sensor.c:486: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c:487: error: ‘struct <anonymous>’ has no member named ‘secondsInAccumulator’
../../common/sensor.c:488: error: ‘struct <anonymous>’ has no member named ‘sum’
../../common/sensor.c: In function ‘sensorAccumExit’:
../../common/sensor.c:496: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c:498: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c: In function ‘sensorAccumAddSample’:
../../common/sensor.c:515: error: ‘WV_ACCUM_SAMPLE’ has no member named ‘value’
../../common/sensor.c:516: error: ‘WV_ACCUM_SAMPLE’ has no member named ‘sampleTime’
../../common/sensor.c:517: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c:517: error: ‘NODE_PTR’ undeclared (first use in this function)
../../common/sensor.c:517: error: expected ‘)’ before ‘newNode’
../../common/sensor.c: In function ‘sensorAccumGetTotal’:
../../common/sensor.c:531: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c:533: error: ‘struct <anonymous>’ has no member named ‘samples’
../../common/sensor.c:533: error: ‘NODE_PTR’ undeclared (first use in this function)
../../common/sensor.c:533: error: expected ‘)’ before ‘nodePtr’
../../common/sensor.c:535: error: ‘WV_ACCUM_SAMPLE’ has no member named ‘value’
../../common/sensor.c: In function ‘sensorAccumGetAverage’:
../../common/sensor.c:546: error: ‘struct <anonymous>’ has no member named ‘samples’
make[2]: *** [sensor.o] Error 1
make[2]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/Simulator'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations'
make: *** [install-recursive] Error 1

Please help! :confused:

---

### Post by Partyboi2 on 2009-06-11
Hi, looks like you don't have the radlib library installed, go to
[http://www.radlib.teel.ws/](http://www.radlib.teel.ws/) and download and compile
```
tar xvzf radlib-2.8.2.tar.gz 
cd  radlib-2.8.2/
./configure --enable-sqlite
make
sudo make install
```then  go back to wview and run
```
./configure
make
sudo make install
```

---

### Post by NDBrinkley on 2009-06-11
Thanks very much for your reply partyboi2.
I tried exactly what you suggested and ./configure seemed to run ok. However when I ran 'make', it returned:

make  all-recursive
make[1]: Entering directory `/home/ndbrinkley/radlib-2.8.2'
Making all in src
make[2]: Entering directory `/home/ndbrinkley/radlib-2.8.2/src'
make[3]: Entering directory `/home/ndbrinkley/radlib-2.8.2/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I.. -I../h -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE   -I/usr/local/include -I/usr/include    -g -O2 -MT radsqlite.lo -MD -MP -MF .deps/radsqlite.Tpo -c -o radsqlite.lo `test -f '../src/radsqlite.c' || echo './'`../src/radsqlite.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -I../h -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -I/usr/local/include -I/usr/include -g -O2 -MT radsqlite.lo -MD -MP -MF .deps/radsqlite.Tpo -c ../src/radsqlite.c  -fPIC -DPIC -o .libs/radsqlite.o
In file included from ../src/radsqlite.c:48:
../h/radsqlite.h:69:21: error: sqlite3.h: No such file or directory
In file included from ../src/radsqlite.c:48:
../h/radsqlite.h:89: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../h/radsqlite.h:509: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘radsqlitedirectGetRow’
../h/radsqlite.h:527: error: expected ‘)’ before ‘id’
../src/radsqlite.c:67: error: expected specifier-qualifier-list before ‘sqlite3’
../src/radsqlite.c: In function ‘printError’:
../src/radsqlite.c:81: error: ‘struct <anonymous>’ has no member named ‘dbConn’
../src/radsqlite.c:81: error: ‘struct <anonymous>’ has no member named ‘dbConn’
../src/radsqlite.c:81: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
../src/radsqlite.c: At top level:
../src/radsqlite.c:118: error: expected declaration specifiers or ‘...’ before ‘sqlite3_stmt’
../src/radsqlite.c: In function ‘processResultRow’:
../src/radsqlite.c:134: error: ‘statement’ undeclared (first use in this function)
../src/radsqlite.c:134: error: (Each undeclared identifier is reported only once
../src/radsqlite.c:134: error: for each function it appears in.)
../src/radsqlite.c:148: warning: passing argument 2 of ‘strncpy’ makes pointer from integer without a cast
../src/radsqlite.c:152: error: ‘SQLITE_INTEGER’ undeclared (first use in this function)
../src/radsqlite.c:157: error: ‘SQLITE_FLOAT’ undeclared (first use in this function)
../src/radsqlite.c:162: error: ‘SQLITE_NULL’ undeclared (first use in this function)
../src/radsqlite.c:165: error: ‘SQLITE_TEXT’ undeclared (first use in this function)
../src/radsqlite.c:175: warning: passing argument 2 of ‘memcpy’ makes pointer from integer without a cast
../src/radsqlite.c:186: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c: In function ‘radsqliteOpen’:
../src/radsqlite.c:215: error: ‘struct <anonymous>’ has no member named ‘dbConn’
../src/radsqlite.c:215: error: ‘SQLITE_OK’ undeclared (first use in this function)
../src/radsqlite.c:220: error: ‘struct <anonymous>’ has no member named ‘dbConn’
../src/radsqlite.c:222: error: ‘struct <anonymous>’ has no member named ‘dbConn’
../src/radsqlite.c:223: error: ‘struct <anonymous>’ has no member named ‘dbConn’
../src/radsqlite.c: In function ‘radsqliteClose’:
../src/radsqlite.c:240: error: ‘struct <anonymous>’ has no member named ‘dbConn’
../src/radsqlite.c:240: error: ‘SQLITE_OK’ undeclared (first use in this function)
../src/radsqlite.c:245: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:247: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c: In function ‘radsqliteQuery’:
../src/radsqlite.c:274: error: ‘sqlite3_stmt’ undeclared (first use in this function)
../src/radsqlite.c:274: error: ‘statement’ undeclared (first use in this function)
../src/radsqlite.c:286: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:290: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:290: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:291: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:297: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:297: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:298: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:299: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:306: error: ‘struct <anonymous>’ has no member named ‘dbConn’
../src/radsqlite.c:311: error: ‘SQLITE_OK’ undeclared (first use in this function)
../src/radsqlite.c:316: error: ‘SQLITE_BUSY’ undeclared (first use in this function)
../src/radsqlite.c:316: error: ‘SQLITE_LOCKED’ undeclared (first use in this function)
../src/radsqlite.c:327: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:328: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:338: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:339: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:349: error: ‘SQLITE_ROW’ undeclared (first use in this function)
../src/radsqlite.c:352: error: too many arguments to function ‘processResultRow’
../src/radsqlite.c:357: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:358: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:364: error: ‘SQLITE_DONE’ undeclared (first use in this function)
../src/radsqlite.c:372: error: ‘SQLITE_ERROR’ undeclared (first use in this function)
../src/radsqlite.c:373: error: ‘SQLITE_MISUSE’ undeclared (first use in this function)
../src/radsqlite.c:380: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:381: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:393: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c: In function ‘radsqliteGetResults’:
../src/radsqlite.c:417: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c: In function ‘radsqliteReleaseResults’:
../src/radsqlite.c:474: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c: In function ‘radsqlitedirectQuery’:
../src/radsqlite.c:1462: error: ‘sqlite3_stmt’ undeclared (first use in this function)
../src/radsqlite.c:1462: error: ‘statement’ undeclared (first use in this function)
../src/radsqlite.c:1474: error: ‘struct <anonymous>’ has no member named ‘resSet’
../src/radsqlite.c:1475: error: ‘struct <anonymous>’ has no member named ‘statement’
../src/radsqlite.c:1481: error: ‘struct <anonymous>’ has no member named ‘dbConn’
../src/radsqlite.c:1486: error: ‘SQLITE_OK’ undeclared (first use in this function)
../src/radsqlite.c:1491: error: ‘SQLITE_BUSY’ undeclared (first use in this function)
../src/radsqlite.c:1491: error: ‘SQLITE_LOCKED’ undeclared (first use in this function)
../src/radsqlite.c:1514: error: ‘struct <anonymous>’ has no member named ‘statement’
../src/radsqlite.c: At top level:
../src/radsqlite.c:1527: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘radsqlitedirectGetRow’
../src/radsqlite.c: In function ‘radsqlitedirectReleaseResults’:
../src/radsqlite.c:1575: error: ‘struct <anonymous>’ has no member named ‘statement’
../src/radsqlite.c:1577: error: ‘struct <anonymous>’ has no member named ‘statement’
../src/radsqlite.c:1578: error: ‘struct <anonymous>’ has no member named ‘statement’
../src/radsqlite.c: At top level:
../src/radsqlite.c:1588: error: expected ‘)’ before ‘statement’
make[3]: *** [radsqlite.lo] Error 1
make[3]: Leaving directory `/home/ndbrinkley/radlib-2.8.2/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ndbrinkley/radlib-2.8.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ndbrinkley/radlib-2.8.2'
make: *** [all] Error 2

I'm sure I am doing something wrong as this looks rather similar to the output when I try to 'make' wview-5.5.0.
Any ideas?

Thanks

---

### Post by Partyboi2 on 2009-06-11
You need the libsqlite3-dev package, install it with
```
sudo apt-get install libsqlite3-dev
```
then back in the wview directory
```
./configure
make 
sudo make install
```

---

### Post by NDBrinkley on 2009-06-12
Thanks again for your help. I have installed:
libz
libpng
libgd2
libreadline5
libsqlite3

In the WView directory I run:
```
./configure
make
sudo make install
```

It still returns:
```

make[4]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/WXT510'
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT sensor.o -MD -MP -MF .deps/sensor.Tpo -c -o sensor.o `test -f '../../common/sensor.c' || echo './'`../../common/sensor.c
mv -f .deps/sensor.Tpo .deps/sensor.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT wvutils.o -MD -MP -MF .deps/wvutils.Tpo -c -o wvutils.o `test -f '../../common/wvutils.c' || echo './'`../../common/wvutils.c
mv -f .deps/wvutils.Tpo .deps/wvutils.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT wvconfig.o -MD -MP -MF .deps/wvconfig.Tpo -c -o wvconfig.o `test -f '../../common/wvconfig.c' || echo './'`../../common/wvconfig.c
mv -f .deps/wvconfig.Tpo .deps/wvconfig.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT dbsqlite.o -MD -MP -MF .deps/dbsqlite.Tpo -c -o dbsqlite.o `test -f '../../common/dbsqlite.c' || echo './'`../../common/dbsqlite.c
mv -f .deps/dbsqlite.Tpo .deps/dbsqlite.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT dbsqliteHiLow.o -MD -MP -MF .deps/dbsqliteHiLow.Tpo -c -o dbsqliteHiLow.o `test -f '../../common/dbsqliteHiLow.c' || echo './'`../../common/dbsqliteHiLow.c
mv -f .deps/dbsqliteHiLow.Tpo .deps/dbsqliteHiLow.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT windAverage.o -MD -MP -MF .deps/windAverage.Tpo -c -o windAverage.o `test -f '../../common/windAverage.c' || echo './'`../../common/windAverage.c
mv -f .deps/windAverage.Tpo .deps/windAverage.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT emailAlerts.o -MD -MP -MF .deps/emailAlerts.Tpo -c -o emailAlerts.o `test -f '../../common/emailAlerts.c' || echo './'`../../common/emailAlerts.c
mv -f .deps/emailAlerts.Tpo .deps/emailAlerts.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT computedData.o -MD -MP -MF .deps/computedData.Tpo -c -o computedData.o `test -f '../../stations/common/computedData.c' || echo './'`../../stations/common/computedData.c
mv -f .deps/computedData.Tpo .deps/computedData.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT daemon.o -MD -MP -MF .deps/daemon.Tpo -c -o daemon.o `test -f '../../stations/common/daemon.c' || echo './'`../../stations/common/daemon.c
mv -f .deps/daemon.Tpo .deps/daemon.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT station.o -MD -MP -MF .deps/station.Tpo -c -o station.o `test -f '../../stations/common/station.c' || echo './'`../../stations/common/station.c
mv -f .deps/station.Tpo .deps/station.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT serial.o -MD -MP -MF .deps/serial.Tpo -c -o serial.o `test -f '../../stations/common/serial.c' || echo './'`../../stations/common/serial.c
mv -f .deps/serial.Tpo .deps/serial.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT ethernet.o -MD -MP -MF .deps/ethernet.Tpo -c -o ethernet.o `test -f '../../stations/common/ethernet.c' || echo './'`../../stations/common/ethernet.c
mv -f .deps/ethernet.Tpo .deps/ethernet.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT stormRain.o -MD -MP -MF .deps/stormRain.Tpo -c -o stormRain.o `test -f '../../stations/common/stormRain.c' || echo './'`../../stations/common/stormRain.c
mv -f .deps/stormRain.Tpo .deps/stormRain.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT parser.o -MD -MP -MF .deps/parser.Tpo -c -o parser.o `test -f '../../stations/common/parser.c' || echo './'`../../stations/common/parser.c
mv -f .deps/parser.Tpo .deps/parser.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT wxt510Interface.o -MD -MP -MF .deps/wxt510Interface.Tpo -c -o wxt510Interface.o `test -f '../../stations/WXT510/wxt510Interface.c' || echo './'`../../stations/WXT510/wxt510Interface.c
mv -f .deps/wxt510Interface.Tpo .deps/wxt510Interface.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT nmea0183.o -MD -MP -MF .deps/nmea0183.Tpo -c -o nmea0183.o `test -f '../../stations/WXT510/nmea0183.c' || echo './'`../../stations/WXT510/nmea0183.c
mv -f .deps/nmea0183.Tpo .deps/nmea0183.Po
gcc  -g -O2 -L/usr/lib -L/usr/local/lib -L/usr/local/lib  -o wviewd_wxt510 sensor.o wvutils.o wvconfig.o dbsqlite.o dbsqliteHiLow.o windAverage.o emailAlerts.o computedData.o daemon.o station.o serial.o ethernet.o stormRain.o parser.o wxt510Interface.o nmea0183.o -lc -lm -lrad -lsqlite3 -lz -lrad -lsqlite3 -lpng -lm -lc 
make[4]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/WXT510'
make[3]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/WXT510'
Making all in WS-2300
make[3]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/WS-2300'
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT sensor.o -MD -MP -MF .deps/sensor.Tpo -c -o sensor.o `test -f '../../common/sensor.c' || echo './'`../../common/sensor.c
mv -f .deps/sensor.Tpo .deps/sensor.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT wvutils.o -MD -MP -MF .deps/wvutils.Tpo -c -o wvutils.o `test -f '../../common/wvutils.c' || echo './'`../../common/wvutils.c
mv -f .deps/wvutils.Tpo .deps/wvutils.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT wvconfig.o -MD -MP -MF .deps/wvconfig.Tpo -c -o wvconfig.o `test -f '../../common/wvconfig.c' || echo './'`../../common/wvconfig.c
mv -f .deps/wvconfig.Tpo .deps/wvconfig.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT dbsqlite.o -MD -MP -MF .deps/dbsqlite.Tpo -c -o dbsqlite.o `test -f '../../common/dbsqlite.c' || echo './'`../../common/dbsqlite.c
mv -f .deps/dbsqlite.Tpo .deps/dbsqlite.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT dbsqliteHiLow.o -MD -MP -MF .deps/dbsqliteHiLow.Tpo -c -o dbsqliteHiLow.o `test -f '../../common/dbsqliteHiLow.c' || echo './'`../../common/dbsqliteHiLow.c
mv -f .deps/dbsqliteHiLow.Tpo .deps/dbsqliteHiLow.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT windAverage.o -MD -MP -MF .deps/windAverage.Tpo -c -o windAverage.o `test -f '../../common/windAverage.c' || echo './'`../../common/windAverage.c
mv -f .deps/windAverage.Tpo .deps/windAverage.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT emailAlerts.o -MD -MP -MF .deps/emailAlerts.Tpo -c -o emailAlerts.o `test -f '../../common/emailAlerts.c' || echo './'`../../common/emailAlerts.c
mv -f .deps/emailAlerts.Tpo .deps/emailAlerts.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT computedData.o -MD -MP -MF .deps/computedData.Tpo -c -o computedData.o `test -f '../../stations/common/computedData.c' || echo './'`../../stations/common/computedData.c
mv -f .deps/computedData.Tpo .deps/computedData.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT daemon.o -MD -MP -MF .deps/daemon.Tpo -c -o daemon.o `test -f '../../stations/common/daemon.c' || echo './'`../../stations/common/daemon.c
mv -f .deps/daemon.Tpo .deps/daemon.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT station.o -MD -MP -MF .deps/station.Tpo -c -o station.o `test -f '../../stations/common/station.c' || echo './'`../../stations/common/station.c
mv -f .deps/station.Tpo .deps/station.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT serial.o -MD -MP -MF .deps/serial.Tpo -c -o serial.o `test -f '../../stations/common/serial.c' || echo './'`../../stations/common/serial.c
mv -f .deps/serial.Tpo .deps/serial.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT ethernet.o -MD -MP -MF .deps/ethernet.Tpo -c -o ethernet.o `test -f '../../stations/common/ethernet.c' || echo './'`../../stations/common/ethernet.c
mv -f .deps/ethernet.Tpo .deps/ethernet.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT stormRain.o -MD -MP -MF .deps/stormRain.Tpo -c -o stormRain.o `test -f '../../stations/common/stormRain.c' || echo './'`../../stations/common/stormRain.c
mv -f .deps/stormRain.Tpo .deps/stormRain.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT parser.o -MD -MP -MF .deps/parser.Tpo -c -o parser.o `test -f '../../stations/common/parser.c' || echo './'`../../stations/common/parser.c
mv -f .deps/parser.Tpo .deps/parser.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT ws2300Interface.o -MD -MP -MF .deps/ws2300Interface.Tpo -c -o ws2300Interface.o `test -f '../../stations/WS-2300/ws2300Interface.c' || echo './'`../../stations/WS-2300/ws2300Interface.c
mv -f .deps/ws2300Interface.Tpo .deps/ws2300Interface.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT ws2300protocol.o -MD -MP -MF .deps/ws2300protocol.Tpo -c -o ws2300protocol.o `test -f '../../stations/WS-2300/ws2300protocol.c' || echo './'`../../stations/WS-2300/ws2300protocol.c
mv -f .deps/ws2300protocol.Tpo .deps/ws2300protocol.Po
gcc  -g -O2 -L/usr/lib -L/usr/local/lib -L/usr/local/lib  -o wviewd_ws2300 sensor.o wvutils.o wvconfig.o dbsqlite.o dbsqliteHiLow.o windAverage.o emailAlerts.o computedData.o daemon.o station.o serial.o ethernet.o stormRain.o parser.o ws2300Interface.o ws2300protocol.o -lc -lm -lrad -lsqlite3 -lz -lrad -lsqlite3 -lpng -lm -lc 
make[3]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/WS-2300'
Making all in WMR918
make[3]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/WMR918'
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT sensor.o -MD -MP -MF .deps/sensor.Tpo -c -o sensor.o `test -f '../../common/sensor.c' || echo './'`../../common/sensor.c
mv -f .deps/sensor.Tpo .deps/sensor.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT wvutils.o -MD -MP -MF .deps/wvutils.Tpo -c -o wvutils.o `test -f '../../common/wvutils.c' || echo './'`../../common/wvutils.c
mv -f .deps/wvutils.Tpo .deps/wvutils.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT wvconfig.o -MD -MP -MF .deps/wvconfig.Tpo -c -o wvconfig.o `test -f '../../common/wvconfig.c' || echo './'`../../common/wvconfig.c
mv -f .deps/wvconfig.Tpo .deps/wvconfig.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT dbsqlite.o -MD -MP -MF .deps/dbsqlite.Tpo -c -o dbsqlite.o `test -f '../../common/dbsqlite.c' || echo './'`../../common/dbsqlite.c
mv -f .deps/dbsqlite.Tpo .deps/dbsqlite.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT dbsqliteHiLow.o -MD -MP -MF .deps/dbsqliteHiLow.Tpo -c -o dbsqliteHiLow.o `test -f '../../common/dbsqliteHiLow.c' || echo './'`../../common/dbsqliteHiLow.c
mv -f .deps/dbsqliteHiLow.Tpo .deps/dbsqliteHiLow.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT windAverage.o -MD -MP -MF .deps/windAverage.Tpo -c -o windAverage.o `test -f '../../common/windAverage.c' || echo './'`../../common/windAverage.c
mv -f .deps/windAverage.Tpo .deps/windAverage.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT emailAlerts.o -MD -MP -MF .deps/emailAlerts.Tpo -c -o emailAlerts.o `test -f '../../common/emailAlerts.c' || echo './'`../../common/emailAlerts.c
mv -f .deps/emailAlerts.Tpo .deps/emailAlerts.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT computedData.o -MD -MP -MF .deps/computedData.Tpo -c -o computedData.o `test -f '../../stations/common/computedData.c' || echo './'`../../stations/common/computedData.c
mv -f .deps/computedData.Tpo .deps/computedData.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT daemon.o -MD -MP -MF .deps/daemon.Tpo -c -o daemon.o `test -f '../../stations/common/daemon.c' || echo './'`../../stations/common/daemon.c
mv -f .deps/daemon.Tpo .deps/daemon.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT station.o -MD -MP -MF .deps/station.Tpo -c -o station.o `test -f '../../stations/common/station.c' || echo './'`../../stations/common/station.c
mv -f .deps/station.Tpo .deps/station.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT serial.o -MD -MP -MF .deps/serial.Tpo -c -o serial.o `test -f '../../stations/common/serial.c' || echo './'`../../stations/common/serial.c
mv -f .deps/serial.Tpo .deps/serial.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT ethernet.o -MD -MP -MF .deps/ethernet.Tpo -c -o ethernet.o `test -f '../../stations/common/ethernet.c' || echo './'`../../stations/common/ethernet.c
mv -f .deps/ethernet.Tpo .deps/ethernet.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT stormRain.o -MD -MP -MF .deps/stormRain.Tpo -c -o stormRain.o `test -f '../../stations/common/stormRain.c' || echo './'`../../stations/common/stormRain.c
mv -f .deps/stormRain.Tpo .deps/stormRain.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT parser.o -MD -MP -MF .deps/parser.Tpo -c -o parser.o `test -f '../../stations/common/parser.c' || echo './'`../../stations/common/parser.c
mv -f .deps/parser.Tpo .deps/parser.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT wmr918Interface.o -MD -MP -MF .deps/wmr918Interface.Tpo -c -o wmr918Interface.o `test -f '../../stations/WMR918/wmr918Interface.c' || echo './'`../../stations/WMR918/wmr918Interface.c
mv -f .deps/wmr918Interface.Tpo .deps/wmr918Interface.Po
gcc -DHAVE_CONFIG_H -I. -I../.. -I../../common -I../../stations/common -I/usr/local/include -DHOST_IS_BIGENDIAN=0 -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_WVIEWD    -g -O2 -MT wmr918protocol.o -MD -MP -MF .deps/wmr918protocol.Tpo -c -o wmr918protocol.o `test -f '../../stations/WMR918/wmr918protocol.c' || echo './'`../../stations/WMR918/wmr918protocol.c
mv -f .deps/wmr918protocol.Tpo .deps/wmr918protocol.Po
gcc  -g -O2 -L/usr/lib -L/usr/local/lib -L/usr/local/lib  -o wviewd_wmr918 sensor.o wvutils.o wvconfig.o dbsqlite.o dbsqliteHiLow.o windAverage.o emailAlerts.o computedData.o daemon.o station.o serial.o ethernet.o stormRain.o parser.o wmr918Interface.o wmr918protocol.o -lc -lm -lrad -lsqlite3 -lz -lrad -lsqlite3 -lpng -lm -lc 
make[3]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/WMR918'
make[3]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations'
make[2]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations'
Making all in htmlgenerator
make[2]: Entering directory `/home/ndbrinkley/wview-5.5.0/htmlgenerator'
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I/usr/local/include -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_HTMLGEND    -g -O2 -MT sensor.o -MD -MP -MF .deps/sensor.Tpo -c -o sensor.o `test -f '../common/sensor.c' || echo './'`../common/sensor.c
mv -f .deps/sensor.Tpo .deps/sensor.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I/usr/local/include -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_HTMLGEND    -g -O2 -MT wvutils.o -MD -MP -MF .deps/wvutils.Tpo -c -o wvutils.o `test -f '../common/wvutils.c' || echo './'`../common/wvutils.c
mv -f .deps/wvutils.Tpo .deps/wvutils.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I/usr/local/include -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_HTMLGEND    -g -O2 -MT wvconfig.o -MD -MP -MF .deps/wvconfig.Tpo -c -o wvconfig.o `test -f '../common/wvconfig.c' || echo './'`../common/wvconfig.c
mv -f .deps/wvconfig.Tpo .deps/wvconfig.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I/usr/local/include -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_HTMLGEND    -g -O2 -MT lunarCycle.o -MD -MP -MF .deps/lunarCycle.Tpo -c -o lunarCycle.o `test -f '../common/lunarCycle.c' || echo './'`../common/lunarCycle.c
mv -f .deps/lunarCycle.Tpo .deps/lunarCycle.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I/usr/local/include -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_HTMLGEND    -g -O2 -MT sunTimes.o -MD -MP -MF .deps/sunTimes.Tpo -c -o sunTimes.o `test -f '../common/sunTimes.c' || echo './'`../common/sunTimes.c
mv -f .deps/sunTimes.Tpo .deps/sunTimes.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I/usr/local/include -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_HTMLGEND    -g -O2 -MT dbsqlite.o -MD -MP -MF .deps/dbsqlite.Tpo -c -o dbsqlite.o `test -f '../common/dbsqlite.c' || echo './'`../common/dbsqlite.c
mv -f .deps/dbsqlite.Tpo .deps/dbsqlite.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I/usr/local/include -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_HTMLGEND    -g -O2 -MT dbsqliteHistory.o -MD -MP -MF .deps/dbsqliteHistory.Tpo -c -o dbsqliteHistory.o `test -f '../common/dbsqliteHistory.c' || echo './'`../common/dbsqliteHistory.c
mv -f .deps/dbsqliteHistory.Tpo .deps/dbsqliteHistory.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I/usr/local/include -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_HTMLGEND    -g -O2 -MT dbsqliteHiLow.o -MD -MP -MF .deps/dbsqliteHiLow.Tpo -c -o dbsqliteHiLow.o `test -f '../common/dbsqliteHiLow.c' || echo './'`../common/dbsqliteHiLow.c
mv -f .deps/dbsqliteHiLow.Tpo .deps/dbsqliteHiLow.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I/usr/local/include -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_HTMLGEND    -g -O2 -MT dbsqliteNOAA.o -MD -MP -MF .deps/dbsqliteNOAA.Tpo -c -o dbsqliteNOAA.o `test -f '../common/dbsqliteNOAA.c' || echo './'`../common/dbsqliteNOAA.c
mv -f .deps/dbsqliteNOAA.Tpo .deps/dbsqliteNOAA.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I/usr/local/include -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_HTMLGEND    -g -O2 -MT windAverage.o -MD -MP -MF .deps/windAverage.Tpo -c -o windAverage.o `test -f '../common/windAverage.c' || echo './'`../common/windAverage.c
mv -f .deps/windAverage.Tpo .deps/windAverage.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I/usr/local/include -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_HTMLGEND    -g -O2 -MT emailAlerts.o -MD -MP -MF .deps/emailAlerts.Tpo -c -o emailAlerts.o `test -f '../common/emailAlerts.c' || echo './'`../common/emailAlerts.c
mv -f .deps/emailAlerts.Tpo .deps/emailAlerts.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I/usr/local/include -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_HTMLGEND    -g -O2 -MT html.o -MD -MP -MF .deps/html.Tpo -c -o html.o `test -f '../htmlgenerator/html.c' || echo './'`../htmlgenerator/html.c
mv -f .deps/html.Tpo .deps/html.Po
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I/usr/local/include -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_HTMLGEND    -g -O2 -MT htmlStates.o -MD -MP -MF .deps/htmlStates.Tpo -c -o htmlStates.o `test -f '../htmlgenerator/htmlStates.c' || echo './'`../htmlgenerator/htmlStates.c
In file included from ../htmlgenerator/htmlStates.c:35:
./glchart.h:28:16: error: gd.h: No such file or directory
In file included from ../htmlgenerator/htmlStates.c:35:
./glchart.h:60: error: expected specifier-qualifier-list before ‘gdImagePtr’
make[2]: *** [htmlStates.o] Error 1
make[2]: Leaving directory `/home/ndbrinkley/wview-5.5.0/htmlgenerator'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ndbrinkley/wview-5.5.0'
make: *** [all] Error 2
ndbrinkley@home:~/wview-5.5.0$ sudo make install
Making install in stations
make[1]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations'
Making install in Simulator
make[2]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/Simulator'
make[3]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/Simulator'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'wviewd_sim' '/usr/local/bin/wviewd_sim'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/Simulator'
make[2]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/Simulator'
Making install in VantagePro
make[2]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/VantagePro'
Making install in vpconfig
make[3]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/VantagePro/vpconfig'
make[4]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/VantagePro/vpconfig'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'vpconfig' '/usr/local/bin/vpconfig'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
 /usr/bin/install -c 'vpinstall' '/usr/local/bin/vpinstall'
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/VantagePro/vpconfig'
make[3]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/VantagePro/vpconfig'
make[3]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/VantagePro'
make[4]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/VantagePro'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'wviewd_vpro' '/usr/local/bin/wviewd_vpro'
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/VantagePro'
make[3]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/VantagePro'
make[2]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/VantagePro'
Making install in WXT510
make[2]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/WXT510'
Making install in wxt510config
make[3]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/WXT510/wxt510config'
make[4]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/WXT510/wxt510config'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'wxt510config' '/usr/local/bin/wxt510config'
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/WXT510/wxt510config'
make[3]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/WXT510/wxt510config'
make[3]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/WXT510'
make[4]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/WXT510'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'wviewd_wxt510' '/usr/local/bin/wviewd_wxt510'
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/WXT510'
make[3]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/WXT510'
make[2]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/WXT510'
Making install in WS-2300
make[2]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/WS-2300'
make[3]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/WS-2300'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'wviewd_ws2300' '/usr/local/bin/wviewd_ws2300'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/WS-2300'
make[2]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/WS-2300'
Making install in WMR918
make[2]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/WMR918'
make[3]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations/WMR918'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'wviewd_wmr918' '/usr/local/bin/wviewd_wmr918'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/WMR918'
make[2]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/WMR918'
make[2]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations'
make[3]: Entering directory `/home/ndbrinkley/wview-5.5.0/stations'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations'
make[2]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations'
make[1]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations'
Making install in htmlgenerator
make[1]: Entering directory `/home/ndbrinkley/wview-5.5.0/htmlgenerator'
gcc -DHAVE_CONFIG_H -I. -I.. -I../common -I/usr/local/include -D_GNU_SOURCE -DWV_CONFIG_DIR=\"/usr/local/etc/wview\" -DWV_RUN_DIR=\"/usr/local/var/wview\" -DBUILD_HTMLGEND    -g -O2 -MT htmlStates.o -MD -MP -MF .deps/htmlStates.Tpo -c -o htmlStates.o `test -f '../htmlgenerator/htmlStates.c' || echo './'`../htmlgenerator/htmlStates.c
In file included from ../htmlgenerator/htmlStates.c:35:
./glchart.h:28:16: error: gd.h: No such file or directory
In file included from ../htmlgenerator/htmlStates.c:35:
./glchart.h:60: error: expected specifier-qualifier-list before ‘gdImagePtr’
make[1]: *** [htmlStates.o] Error 1
make[1]: Leaving directory `/home/ndbrinkley/wview-5.5.0/htmlgenerator'
make: *** [install-recursive] Error 1

```

Then seems to do nothing. Has it installed? If so, how do I run it? I really can't see what is wrong. Sorry to keep posting on this. Any further help would be really appreciated. :confused:

---

### Post by Partyboi2 on 2009-06-12
> ./glchart.h:28:16: error: gd.h: No such file or directory
try installing libgd2-xpm-dev.
```
sudo apt-get install libgd2-xpm-dev
```
then back in the WView directory
```
./configure
make
sudo make install
```

[B]
[/B]

---

### Post by NDBrinkley on 2009-06-12
Thanks

libgd2-xpm-dev is installed now

In wview-5.5.0 I entered:

```
./configure
make
sudo make install
```

Part of what was returned contained:

> ../../common/wvconfig.h:43:23: error: radsqlite.h: No such file or directory
make[2]: *** [wvutils.o] Error 1
make[2]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/Simulator'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations'
make: *** [install-recursive] Error 1

I can't figure out what radsqlite.h is.

What should happen when it has installed correctly, enter a shortcut to the menu or place an executable in the wview directory?

---

### Post by Partyboi2 on 2009-06-13
When you compiled radlib did you enable sqlite?
> tar xvzf radlib-2.8.2.tar.gz 
cd  radlib-2.8.2/
./configure --enable-sqlite
make
sudo make install
> What should happen when it has installed correctly, enter a shortcut to the menu or place an executable in the wview directory? 	
I am not completely sure, it looks like you might need to run it through the terminal.  I have not really had a good look at Wview and how to set it up to be honest.

---

### Post by NDBrinkley on 2009-06-17
Yes and it returned:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking whether byte ordering is bigendian... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for strncpy in -lc... yes
checking for exp in -lm... yes
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for pid_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking return type of signal handlers... void
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for vprintf... yes
checking for _doprnt... no
checking for getcwd... yes
checking for gethostname... yes
checking for gettimeofday... yes
checking for memset... yes
checking for mkdir... yes
checking for mkfifo... yes
checking for select... yes
checking for strchr... yes
checking for strerror... yes
checking for strrchr... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating msgRouter/Makefile
config.status: creating debug/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

```

Though wview still gives:
```
../../common/wvconfig.h:43:23: error: radsqlite.h: No such file or directory
make[2]: *** [wvutils.o] Error 1
make[2]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations/Simulator'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/ndbrinkley/wview-5.5.0/stations'
make: *** [install-recursive] Error 1 
```
I really need wview to work and it's starting to drive me mad!#-o
Thanks again

---

### Post by mteel on 2009-06-20
This build error definitely indicates that radlib was not built with sqlite3 support.

```
From radlib source directory:
> sudo make distclean
> ./configure --enable-sqlite
> sudo make install

```
```
Then back to the wview source directory:
> sudo make distclean
> HTTP_DOC_ROOT=/var/www ./configure --enable-station-sim
> sudo make install-env

```
I am guessing where your HTTP server document root is (/var/www). You can change the station type later when configuring wview.

The User Manual is your friend...

---

### Post by NDBrinkley on 2009-06-21
Thanks mteel for your help. I have run what you suggested and all seems to have installed properly.
Then I enter:
```
cp wview-5.5.0/examples/Debian/wview /etc/init.d
chmod +x /etc/init.d/wview
update-rc.d wview defaults 98
```

Then to run program:
```
/etc/init.d/wview start
```

From which I get:
> Starting wview daemons:
radlib router pid file /usr/local/var/wview/radmrouted.pid exists - killing existing process
/etc/init.d/wview: line 58: kill: (12307) - Operation not permitted
rm: cannot remove `/usr/local/var/wview/radmrouted.pid': Permission denied
radmrouted[12740]: <1245626223486> : lock file /usr/local/var/wview/radmrouted.pid exists, older copy may be running - aborting!
wviewd[12742]: <1245626224493> : radSystemInit failed!
htmlgend[12744]: <1245626225500> : system init failed!
wvalarmd[12745]: <1245626225503> : wview daemon lock file /usr/local/var/wview/wviewd.pid does not exist - aborting!
wvcwopd[12746]: <1245626225507> : wview daemon lock file /usr/local/var/wview/wviewd.pid does not exist - aborting!
wvhttpd[12747]: <1245626225514> : wview daemon lock file /usr/local/var/wview/wviewd.pid does not exist - aborting!
wviewftpd[12748]: <1245626225525> : wview daemon lock file /usr/local/var/wview/wviewd.pid does not exist - aborting!
wviewsshd[12749]: <1245626225528> : wview daemon lock file /usr/local/var/wview/wviewd.pid does not exist - aborting!
wvpmond[12750]: <1245626225541> : wview daemon lock file /usr/local/var/wview/wviewd.pid does not exist - aborting!


Sorry but, as you can probably tell, I am a Linux novice. I appreciate you help. :D

---

### Post by mteel on 2009-09-19
Looks like you are running the start script as a user other than root.  It is trying to clean up old PID files lying around from previous failed starts.

Try:
> sudo /etc/init.d/wview start

Mark

---

