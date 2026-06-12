---
title: "Cheese 2.25.4?"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by vegetarianshrimp on 2009-01-17
I was wondering how to install [Cheese 2.25.4]("http://projects.gnome.org/cheese/download") in 8.10 Intrepid 
I saved the file, extracted it to Desktop, then did these commands:
cd Desktop
cd cheese-2.25.4.tar.gz
./configure

I was about to do make and make install, but something went wrong. (look at the bottom of code)
```
daniel@daniel-laptop:~/Desktop/cheese-2.25.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
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
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler... 
checking whether NLS is requested... yes
checking for intltool >= 0.40.0... 0.40.5 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for CHEESE... configure: error: Package requirements (  glib-2.0 >= 2.16.0   gobject-2.0 >= 2.12.0   gio-2.0 >= 2.16.0   gtk+-2.0 >= 2.14.0   gdk-2.0 >= 2.14.0   gnome-desktop-2.0 >= 2.25.1   gconf-2.0 >= 2.16.0   gstreamer-0.10 >= 0.10.20   gstreamer-plugins-base-0.10 >= 0.10.20   libebook-1.2 >= 1.12.0   cairo >= 1.4.0   dbus-1 >= 1.0   dbus-glib-1 >= 0.7   hal >= 0.5.9   pangocairo >= 1.18.0   librsvg-2.0 >= 2.18.0) were not met:

No package 'glib-2.0' found
No package 'gobject-2.0' found
No package 'gio-2.0' found
No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'gnome-desktop-2.0' found
No package 'gconf-2.0' found
No package 'gstreamer-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'libebook-1.2' found
No package 'cairo' found
No package 'dbus-1' found
No package 'dbus-glib-1' found
No package 'hal' found
No package 'pangocairo' found
No package 'librsvg-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CHEESE_CFLAGS
and CHEESE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```Do I need to Install those packages that weren't found?
What do I do?

---

### Post by Partyboi2 on 2009-01-17
You need to install the -dev packages of what is listed
> No package 'glib-2.0' found
No package 'gobject-2.0' found
No package 'gio-2.0' found
No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'gnome-desktop-2.0' found
No package 'gconf-2.0' found
No package 'gstreamer-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'libebook-1.2' found
No package 'cairo' found
No package 'dbus-1' found
No package 'dbus-glib-1' found
No package 'hal' found
No package 'pangocairo' found
No package 'librsvg-2.0' foundAn easy way is to install the dev packages for cheese since it is in the ubuntu repos is to
```
sudo apt-get build-dep cheese
```

---

### Post by vegetarianshrimp on 2009-01-17
I did that, then ran ./configure again. 
I got this:

```
daniel@daniel-laptop:~$ cd Desktop
daniel@daniel-laptop:~/Desktop$ cd cheese-2.25.4
daniel@daniel-laptop:~/Desktop/cheese-2.25.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
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
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler... 
checking whether NLS is requested... yes
checking for intltool >= 0.40.0... 0.40.5 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for CHEESE... configure: error: Package requirements (  glib-2.0 >= 2.16.0   gobject-2.0 >= 2.12.0   gio-2.0 >= 2.16.0   gtk+-2.0 >= 2.14.0   gdk-2.0 >= 2.14.0   gnome-desktop-2.0 >= 2.25.1   gconf-2.0 >= 2.16.0   gstreamer-0.10 >= 0.10.20   gstreamer-plugins-base-0.10 >= 0.10.20   libebook-1.2 >= 1.12.0   cairo >= 1.4.0   dbus-1 >= 1.0   dbus-glib-1 >= 0.7   hal >= 0.5.9   pangocairo >= 1.18.0   librsvg-2.0 >= 2.18.0) were not met:

No package 'gnome-desktop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CHEESE_CFLAGS
and CHEESE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

daniel@daniel-laptop:~/Desktop/cheese-2.25.4$ 

```

---

### Post by Rhubarb on 2009-01-17
I vaguely remember trying to compile the latest cheese a few weeks ago.
I ran into a rather large problem that required gnome 2.26 to be installed, which makes it impossible to get going unless you install gnome 2.26, which is only attainable if you install Ubuntu 9.04 alpha 3.

I have tried using cheese in Ubuntu 9.04 alpha 3, and it does run very nicely then (I had a few problems with cheese that's currently in intrepid - such as low resolution only, crashing when selecting an effect, and not being able to record video).

For me compiling the latest version of cheese in intrepid (ubuntu 8.10) seemed rather impossible.  I gave up trying when I (think) it required the latest version of gnome (which I'm pretty sure is still under development).

---

### Post by vegetarianshrimp on 2009-01-17
Would downloading an OLD version work? (this is all because I want the video to work)

---

### Post by Rhubarb on 2009-01-18
> **vegetarianshrimp said:**
> Would downloading an OLD version work? (this is all because I want the video to work)

I'm not sure, as I think the reason why cheese doesn't work so well (for me anyway) is because of the video4linux2 new stuff, and possibly something to do with gstreamer.  - Which I'm not sure if it'll handle that well running an older version of cheese.

Otherwise I'd suggest you try out Ubuntu 9.04 alpha, and prepare yourself for borkage, or just wait a few months until it is released.

---

### Post by vegetarianshrimp on 2009-01-18
Ya I think I'll wait...

---

### Post by branque on 2009-02-05
Have same problem while trying to run "./configure" at SVN version of Cheese 2.25.4... also tried "sudo apt-get build-dep cheese".

Here is my "./configure" error message...

checking for CHEESE... configure: error: Package requirements (  glib-2.0 >= 2.16.0   gobject-2.0 >= 2.12.0   gio-2.0 >= 2.16.0   gtk+-2.0 >= 2.14.0   gdk-2.0 >= 2.14.0   gnome-desktop-2.0 >= 2.25.1   gconf-2.0 >= 2.16.0   gstreamer-0.10 >= 0.10.20   gstreamer-plugins-base-0.10 >= 0.10.20   libebook-1.2 >= 1.12.0   cairo >= 1.4.0   dbus-1 >= 1.0   dbus-glib-1 >= 0.7   hal >= 0.5.9   pangocairo >= 1.18.0   librsvg-2.0 >= 2.18.0) were not met:

Requested 'gnome-desktop-2.0 >= 2.25.1' but version of gnome-desktop-2.0 is 2.24.1

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CHEESE_CFLAGS
and CHEESE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Because Im using Ubuntu 8.10, last version of libgnome-desktop-dev is 1.14.1. There is a newer version is available, 2.25.5, but due to depends problem, I can not install it.

---

### Post by Partyboi2 on 2009-02-05
> **branque said:**
> Have same problem while trying to run "./configure" at SVN version of Cheese 2.25.4... also tried "sudo apt-get build-dep cheese".

Here is my "./configure" error message...

checking for CHEESE... configure: error: Package requirements (  glib-2.0 >= 2.16.0   gobject-2.0 >= 2.12.0   gio-2.0 >= 2.16.0   gtk+-2.0 >= 2.14.0   gdk-2.0 >= 2.14.0   gnome-desktop-2.0 >= 2.25.1   gconf-2.0 >= 2.16.0   gstreamer-0.10 >= 0.10.20   gstreamer-plugins-base-0.10 >= 0.10.20   libebook-1.2 >= 1.12.0   cairo >= 1.4.0   dbus-1 >= 1.0   dbus-glib-1 >= 0.7   hal >= 0.5.9   pangocairo >= 1.18.0   librsvg-2.0 >= 2.18.0) were not met:

Requested 'gnome-desktop-2.0 >= 2.25.1' but version of gnome-desktop-2.0 is 2.24.1

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CHEESE_CFLAGS
and CHEESE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Because Im using Ubuntu 8.10, last version of libgnome-desktop-dev is 1.14.1. There is a newer version is available, 2.25.5, but due to depends problem, I can not install it.
Have you tried compiling the stable version of cheese 2.24.2 rather then the development one (2.25.4)

---

### Post by branque on 2009-02-10
The reason I want to upgrade Cheese software, is because default version in Ubuntu 8.10, 2.24.2, does not find my webcam, 05ca:1839, witch works fine in other software, such as Skype, aMSN and in "Multimedia Systems Selector", video tab and default input. Have done my part of the troubleshooting and found gnome cheese faq/bug report states I should try a newer version.

---

