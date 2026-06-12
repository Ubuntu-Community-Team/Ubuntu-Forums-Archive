---
title: "Banshee .tar.gz"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by elliotn on 2009-03-21
I have dloaded banshee player, and have install all dependencies, but when I enter ./configure it run
 But when I type ./make install or make I get 
NO TARGETS SPECIFIED AND NO MAKEFILE FOUND. Stop... Plz help

---

### Post by taurus on 2009-03-21
Just remove the ./ in front of the make.

```
make
```

p.s.  Are you sure ./configure ran successfully?  Post the whole output of ./configure.

---

### Post by elliotn on 2009-03-21
```
elliotn@elliotn:~/Desktop/banshee-1-1.4.3$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether NLS is requested... yes
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
checking for intltool >= 0.35.0... 0.40.5 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.0.0... yes (version 2.18.2)
checking for GDK_X11... yes
checking for GST... yes
checking for GST_PBUTILS... yes
checking for BNPX_GTK... yes
checking for X... libraries , headers 
checking for XVIDMODE... no
checking for MONO_MODULE... yes
checking for gmcs... /usr/bin/gmcs
checking for mono... /usr/bin/mono
checking for Mono 2.0 GAC for System.Data.dll... found
checking for Mono 2.0 GAC for System.Web.dll... found
checking for Mono 2.0 GAC for System.Web.Services.dll... found
checking for Mono 2.0 GAC for Mono.Cairo.dll... found
checking for Mono 2.0 GAC for Mono.Data.SqliteClient.dll... found
checking for Mono 2.0 GAC for Mono.Posix.dll... found
checking for Mono 2.0 GAC for ICSharpCode.SharpZipLib.dll... found
checking for NDESK_DBUS_GLIB... yes
checking for NDESK_DBUS... yes
checking for MONO_ADDINS... yes
checking for MONO_ADDINS_SETUP... yes
checking for MONO_ADDINS_GUI... yes
checking for NOTIFY_SHARP... no
no
checking for BOO... yes
checking for monodocer... no
configure: error: You need to install monodoc, or pass --disable-docs to configure to skip documentation installation
elliotn@elliotn:~/Desktop/banshee-1-1.4.3$ make
make: *** No targets specified and no makefile found.  Stop.
elliotn@elliotn:~/Desktop/banshee-1-1.4.3$ 

```

here is what I get

---

### Post by taurus on 2009-03-21
> **elliotn said:**
> ```

checking for NDESK_DBUS_GLIB... yes
checking for NDESK_DBUS... yes
checking for MONO_ADDINS... yes
checking for MONO_ADDINS_SETUP... yes
checking for MONO_ADDINS_GUI... yes
checking for NOTIFY_SHARP... no
no
checking for BOO... yes
checking for monodocer... no
**configure: [COLOR="Red"]error[/COLOR]: You need to install monodoc, or pass --disable-docs to configure to skip documentation installation**
elliotn@elliotn:~/Desktop/banshee-1-1.4.3$ make
make: *** No targets specified and no makefile found.  Stop.
elliotn@elliotn:~/Desktop/banshee-1-1.4.3$ 

```

here is what I get

So, you either need to install monodoc (documentation) first or rerun configure with that option to skip the doc.

```
./configure --disable-docs
```

---

### Post by directhex on 2009-03-21
... what's wrong with the packages in your distro?

---

### Post by elliotn on 2009-03-21
Well I needed to learn to install in tarball but I give up as now taglib-sharp 2.0.3

---

