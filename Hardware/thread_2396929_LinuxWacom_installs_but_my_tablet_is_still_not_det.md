---
title: "LinuxWacom installs but my tablet is still not detected."
date: 2018-07-23
forum: Hardware
---

### Post by lvivtotoro on 2018-07-23
My situation with this driver is almost the same as in [this thread]("https://ubuntuforums.org/showthread.php?t=2245646").
I tried installing all three items, and rebooting after each install.

My tablet is still not being detected on the System Settings, but lsusb outputs the tablet model normally.
```
midnightas@NetMaster:~/Downloads/xf86-input-wacom-master$ if test -x ./autogen.sh; then ./autogen.sh "$@"; else ./configure "$@"; fi && make && sudo make install || echo "Build Failed"autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: Consider adding '-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
src/common.mk:3: warning: source file '$(top_srcdir)/src/xf86Wacom.c' is in a subdirectory,
src/common.mk:3: but option 'subdir-objects' is disabled
src/Makefile.am:28:   'src/common.mk' included from here
automake: warning: possible forward-incompatibility.
automake: At least a source file is in a subdirectory, but the 'subdir-objects'
automake: automake option hasn't been enabled.  For now, the corresponding output
automake: object file(s) will be placed in the top-level directory.  However,
automake: this behaviour will change in future Automake versions: they will
automake: unconditionally cause object files to be placed in the same subdirectory
automake: of the corresponding sources.
automake: You are advised to start using 'subdir-objects' option throughout your
automake: project, to avoid future incompatibilities.
src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmCommon.c' is in a subdirectory,
src/common.mk:3: but option 'subdir-objects' is disabled
src/Makefile.am:28:   'src/common.mk' included from here
src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmConfig.c' is in a subdirectory,
src/common.mk:3: but option 'subdir-objects' is disabled
src/Makefile.am:28:   'src/common.mk' included from here
src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmISDV4.c' is in a subdirectory,
src/common.mk:3: but option 'subdir-objects' is disabled
src/Makefile.am:28:   'src/common.mk' included from here
src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmFilter.c' is in a subdirectory,
src/common.mk:3: but option 'subdir-objects' is disabled
src/Makefile.am:28:   'src/common.mk' included from here
src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmUSB.c' is in a subdirectory,
src/common.mk:3: but option 'subdir-objects' is disabled
src/Makefile.am:28:   'src/common.mk' included from here
src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmXCommand.c' is in a subdirectory,
src/common.mk:3: but option 'subdir-objects' is disabled
src/Makefile.am:28:   'src/common.mk' included from here
src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmValidateDevice.c' is in a subdirectory,
src/common.mk:3: but option 'subdir-objects' is disabled
src/Makefile.am:28:   'src/common.mk' included from here
src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmTouchFilter.c' is in a subdirectory,
src/common.mk:3: but option 'subdir-objects' is disabled
src/Makefile.am:28:   'src/common.mk' included from here
test/../src/common.mk:3: warning: source file '$(top_srcdir)/src/xf86Wacom.c' is in a subdirectory,
test/../src/common.mk:3: but option 'subdir-objects' is disabled
test/Makefile.am:2:   'test/../src/common.mk' included from here
test/../src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmCommon.c' is in a subdirectory,
test/../src/common.mk:3: but option 'subdir-objects' is disabled
test/Makefile.am:2:   'test/../src/common.mk' included from here
test/../src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmConfig.c' is in a subdirectory,
test/../src/common.mk:3: but option 'subdir-objects' is disabled
test/Makefile.am:2:   'test/../src/common.mk' included from here
test/../src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmISDV4.c' is in a subdirectory,
test/../src/common.mk:3: but option 'subdir-objects' is disabled
test/Makefile.am:2:   'test/../src/common.mk' included from here
test/../src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmFilter.c' is in a subdirectory,
test/../src/common.mk:3: but option 'subdir-objects' is disabled
test/Makefile.am:2:   'test/../src/common.mk' included from here
test/../src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmUSB.c' is in a subdirectory,
test/../src/common.mk:3: but option 'subdir-objects' is disabled
test/Makefile.am:2:   'test/../src/common.mk' included from here
test/../src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmXCommand.c' is in a subdirectory,
test/../src/common.mk:3: but option 'subdir-objects' is disabled
test/Makefile.am:2:   'test/../src/common.mk' included from here
test/../src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmValidateDevice.c' is in a subdirectory,
test/../src/common.mk:3: but option 'subdir-objects' is disabled
test/Makefile.am:2:   'test/../src/common.mk' included from here
test/../src/common.mk:3: warning: source file '$(top_srcdir)/src/wcmTouchFilter.c' is in a subdirectory,
test/../src/common.mk:3: but option 'subdir-objects' is disabled
test/Makefile.am:2:   'test/../src/common.mk' included from here
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking how to convert x86_64-pc-linux-gnu file names to x86_64-pc-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for a working dd... /bin/dd
checking how to truncate binary pipes... /bin/dd bs=4096 count=1
checking for mt... mt
checking if mt is a manifest tool... no
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc option to accept ISO C99... none needed
checking whether __clang__ is declared... no
checking whether __INTEL_COMPILER is declared... no
checking whether __SUNPRO_C is declared... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking if gcc supports -Werror=unknown-warning-option... no
checking if gcc supports -Werror=unused-command-line-argument... no
checking if gcc supports -Wall... yes
checking if gcc supports -Wpointer-arith... yes
checking if gcc supports -Wmissing-declarations... yes
checking if gcc supports -Wformat=2... yes
checking if gcc supports -Wstrict-prototypes... yes
checking if gcc supports -Wmissing-prototypes... yes
checking if gcc supports -Wnested-externs... yes
checking if gcc supports -Wbad-function-cast... yes
checking if gcc supports -Wold-style-definition... yes
checking if gcc supports -Wdeclaration-after-statement... yes
checking if gcc supports -Wunused... yes
checking if gcc supports -Wuninitialized... yes
checking if gcc supports -Wshadow... yes
checking if gcc supports -Wmissing-noreturn... yes
checking if gcc supports -Wmissing-format-attribute... yes
checking if gcc supports -Wredundant-decls... yes
checking if gcc supports -Wlogical-op... yes
checking if gcc supports -Werror=implicit... yes
checking if gcc supports -Werror=nonnull... yes
checking if gcc supports -Werror=init-self... yes
checking if gcc supports -Werror=main... yes
checking if gcc supports -Werror=missing-braces... yes
checking if gcc supports -Werror=sequence-point... yes
checking if gcc supports -Werror=return-type... yes
checking if gcc supports -Werror=trigraphs... yes
checking if gcc supports -Werror=array-bounds... yes
checking if gcc supports -Werror=write-strings... yes
checking if gcc supports -Werror=address... yes
checking if gcc supports -Werror=int-to-pointer-cast... yes
checking if gcc supports -Werror=pointer-to-int-cast... yes
checking if gcc supports -pedantic... yes
checking if gcc supports -Werror... yes
checking if gcc supports -Werror=attributes... yes
checking whether make supports nested variables... (cached) yes
checking for doxygen... no
configure: WARNING: doxygen not found - documentation targets will be skipped
checking for rint in -lm... yes
checking for XORG... yes
checking for X11... yes
checking for UDEV... yes
checking for lshal... no
checking for hal-set-property... no
checking if HAL preprobe quirk should be installed... no
checking whether the linker supports -wrap... yes
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating conf/Makefile
config.status: creating doc/Makefile
config.status: creating doc/doxygen.conf
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating include/Makefile
config.status: creating tools/Makefile
config.status: creating test/Makefile
config.status: creating xorg-wacom.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
if test -x ./git-version-gen; then ./git-version-gen -u; fi
xf86-input-wacom-master
make  all-recursive
make[1]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master'
Making all in conf
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/conf'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/conf'
Making all in doc
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/doc'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/doc'
Making all in src
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/src'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/src'
Making all in man
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/man'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/man'
Making all in include
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/include'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/include'
Making all in tools
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/tools'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/tools'
Making all in test
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/test'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/test'
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master'
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master'
make[1]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master'
[sudo] password for midnightas: doodlidoodlidoodoodundundundundahdahdanhaaaahnanentaroadun
if test -x ./git-version-gen; then ./git-version-gen -u; fi
xf86-input-wacom-master
make  install-recursive
make[1]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master'
Making install in conf
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/conf'
make[3]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/conf'
make[3]: Nothing to be done for 'install-exec-am'.
 /bin/mkdir -p '/usr/share/X11/xorg.conf.d'
 /usr/bin/install -c -m 644 70-wacom.conf '/usr/share/X11/xorg.conf.d'
 /bin/mkdir -p '/usr/lib/udev/rules.d'
 /usr/bin/install -c -m 644 wacom.rules '/usr/lib/udev/rules.d'
 /bin/mkdir -p '/usr/lib/systemd/system'
 /usr/bin/install -c -m 644 wacom-inputattach@.service '/usr/lib/systemd/system'
make[3]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/conf'
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/conf'
Making install in doc
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/doc'
make[3]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/doc'
make[3]: Nothing to be done for 'install-exec-am'.
make[3]: Nothing to be done for 'install-data-am'.
make[3]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/doc'
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/doc'
Making install in src
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/src'
make[3]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/src'
make[3]: Nothing to be done for 'install-exec-am'.
 /bin/mkdir -p '/usr/lib/xorg/modules/input'
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   wacom_drv.la '/usr/lib/xorg/modules/input'
libtool: install: /usr/bin/install -c .libs/wacom_drv.so /usr/lib/xorg/modules/input/wacom_drv.so
libtool: install: /usr/bin/install -c .libs/wacom_drv.lai /usr/lib/xorg/modules/input/wacom_drv.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin:/sbin" ldconfig -n /usr/lib/xorg/modules/input
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/xorg/modules/input


If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the '-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the 'LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the 'LD_RUN_PATH' environment variable
     during linking
   - use the '-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to '/etc/ld.so.conf'


See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/src'
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/src'
Making install in man
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/man'
make[3]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/man'
make[3]: Nothing to be done for 'install-exec-am'.
 /bin/mkdir -p '/usr/share/man/man4'
 /usr/bin/install -c -m 644 wacom.4 '/usr/share/man/man4'
 /bin/mkdir -p '/usr/share/man/man1'
 /usr/bin/install -c -m 644 xsetwacom.1 '/usr/share/man/man1'
make[3]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/man'
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/man'
Making install in include
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/include'
make[3]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/include'
make[3]: Nothing to be done for 'install-exec-am'.
 /bin/mkdir -p '/usr/include/xorg'
 /usr/bin/install -c -m 644 Xwacom.h wacom-properties.h isdv4.h wacom-util.h '/usr/include/xorg'
make[3]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/include'
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/include'
Making install in tools
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/tools'
make[3]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/tools'
 /bin/mkdir -p '/usr/bin'
  /bin/bash ../libtool   --mode=install /usr/bin/install -c xsetwacom isdv4-serial-debugger isdv4-serial-inputattach '/usr/bin'
libtool: install: /usr/bin/install -c xsetwacom /usr/bin/xsetwacom
libtool: install: /usr/bin/install -c isdv4-serial-debugger /usr/bin/isdv4-serial-debugger
libtool: install: /usr/bin/install -c isdv4-serial-inputattach /usr/bin/isdv4-serial-inputattach
make[3]: Nothing to be done for 'install-data-am'.
make[3]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/tools'
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/tools'
Making install in test
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/test'
make[3]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master/test'
make[3]: Nothing to be done for 'install-exec-am'.
make[3]: Nothing to be done for 'install-data-am'.
make[3]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/test'
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master/test'
make[2]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master'
make[3]: Entering directory '/home/midnightas/Downloads/xf86-input-wacom-master'
make[3]: Nothing to be done for 'install-exec-am'.
 /bin/mkdir -p '/usr/lib/pkgconfig'
 /usr/bin/install -c -m 644 xorg-wacom.pc '/usr/lib/pkgconfig'
make[3]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master'
make[2]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master'
make[1]: Leaving directory '/home/midnightas/Downloads/xf86-input-wacom-master'
```
This is just from xf86-input-wacom.
None of the other two outputted "Build Failed".

---

### Post by lvivtotoro on 2018-07-24
Bumping, as this is one of the last things keeping me from moving from Windows : P.

---

### Post by wyliecoyoteuk on 2018-07-27
I have the same issue, not found a solution yet, so bump.

---

### Post by mörgæs on 2018-07-28
Both, please post in CODE tags the output from ```
lsusb
``` and ```
uname -a
```

---

### Post by wyliecoyoteuk on 2018-07-29
here you go:
My tablet is detected, but the settings say "no stylus detected"
The tablet does work on my windows laptop, so not a hardware fault.

```
 lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 0d8c:0103 C-Media Electronics, Inc. CM102-A+/102S+ Audio Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 002: ID 05e3:0616 Genesys Logic, Inc. hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 003: ID 056a:0065 Wacom Co., Ltd Bamboo
Bus 008 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
 uname -a
Linux Mainbox 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

```
grep "" /sys/module/wacom*/version
v2.00-0.41.0

```

---

### Post by lvivtotoro on 2018-07-29
From lsusb:
```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hubBus 003 Device 002: ID 047f:c010 Plantronics, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 056a:033e Wacom Co., Ltd 
Bus 001 Device 003: ID 1c4f:0026 SiGma Micro Keyboard
Bus 001 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

uname -a:
```
Linux midnightas 4.4.0-104-generic #127-Ubuntu SMP Mon Dec 11 12:16:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by mörgæs on 2018-07-29
Lvivtotoro, first I would try how the tablet works in a live boot of 18.04.1. Wacom drivers are in quick development. 

Wyliecoyoteuk, I'll have to read a little more. I don't have a suggestion right now.

---

### Post by wyliecoyoteuk on 2018-07-31
Thanks for trying.
There do seem to be a lot of issues with wacom drivers

---

### Post by wyliecoyoteuk on 2018-07-31
Update:
found this in dmesg (afterIi disabled the drm driver logging which flooded it)

wacom: module verification failed: signature and/or required key missing - tainting kernel

---

### Post by wyliecoyoteuk on 2018-08-27
Update:
Tried everything I could find, finally installed 16.04 on a Virtual Machine, and it worked straight away.

A fresh install of 18.04 in a VM actually detects the tablet but not the stylus!

EDIT: both work after a fashion but are basically unusable, in 18.04 GIMP recognises and configures the stylus, but it is pretty uncontrollable.

---

