---
title: "Tablet Features, Fujitsu T4310 partialy working"
date: 2011-09-01
forum: Hardware
---

### Post by limotux on 2011-09-01
Hi, remember me? Of course I still remember you and all the help I got here especially from Favux, who proffessionaly gave valuable help regarding my tablet.
Now, The same tablet but with Debian, I could get it working to some extent, only need help with:
1- Touch and stylus directions
2- Multitouch not working.
Can you help me please?

I  tried several resources, and searching and reading a  lot, I even retried our old thread, tried to edit rotate-wacom.sh, but  no way.

I don't want to go further without an expert's supervision, so I won't mess things up, and make it more difficult to get support.

Now I have fjbtndrv installed and working, screen rotates, as well as fsc-btns-kernel-source, fscd_2.2.1_i386, fscrotd_2.2.1 installed, and rotate-wacom.sh at its original state.
 
I'll really apprecaite your help.

---

### Post by Favux on 2011-09-01
Hi limotux,

What Debian version are you using?  What's the kernel and Xserver version?
```
Xorg -version
```
Which version of xf86-input-wacom?
```
xsetwacom -V
```
So touch/multi-touch isn't working.  What's the problem with the stylus?

---

### Post by limotux on 2011-09-01
Hi Favux, you are always there for rescue! Thanks a lot.

I'm using LMDE (Linux Mint Debian Edition) which is based on debian testing. For further info in case you nead it check [http://www.linuxmint.com](http://www.linuxmint.com)

To answer your questions first, stylus and touch are working, but not multitouch. In tablet mode the screan rotates automatically, buttons on  the screen work. The problem is that touch and stylus move in other directions, even when I point with my fingure or stylus the cursor points somewhere else.

Now, the results of the commands you required:

1- Xorg -version

```
limo@lmde ~ $ Xorg -version

X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.32-5-amd64 i686 Debian
Current Operating System: Linux lmde 3.0.0-1-686-pae #1 SMP Sat Aug 27 16:41:03 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-1-686-pae root=UUID=e74d13e7-7159-4900-a3dc-c1b2db612b78 ro quiet
Build Date: 24 August 2011  09:37:43AM
xorg-server 2:1.10.4-1 (Cyril Brulebois <kibi@debian.org>) 
Current version of pixman: 0.22.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.



```2- xsetwacom -V

```


limo@lmde ~ $ xsetwacom -V
0.10.10
Usage: xsetwacom [options] [command [arguments...]]
Options:
 -h, --help                 - usage
 -v, --verbose              - verbose output
 -V, --version              - version info
 -d, --display "display"  - override default display
 -s, --shell                - generate shell commands for 'get'
 -x, --xconf                - generate xorg.conf lines for 'get'

Commands:
 --list devices             - display detected devices
 --list parameters          - display supported parameters
 --list modifiers           - display supported modifier and specific keys for keystrokes
 --set "device name" parameter [values...] - set device parameter by name
 --get "device name" parameter [param...]  - get current device parameter(s) value by name
limo@lmde ~ $ 



```I hope I won't trouble you this time.
Thanks again for your help.

---

### Post by Favux on 2011-09-01
Alright, what's the output of *xinput list* in a terminal?

Do the stylus and finger work right in *inverted*?

---

### Post by limotux on 2011-09-01
```
limo@lmde ~ $ xinput list
The program 'xinput' is currently not installed.  To run 'xinput' please ask your administrator to install the package 'xinput'
xinput: command not found
limo@lmde ~ $ 

```Not sure what you mean by "inverted".
Touch and stylus work in latop mode and in tablet mode even I keep rotating the screen all around 360 degrees. They just do not point where they should.
p.s. everything works properly in laptop mode, but no multitouch

---

### Post by Favux on 2011-09-01
To turn gestures on try in a terminal:
```
xsetwacom set "device name" Gesture on
```
I was hoping to get the "device name" from xinput list.  We should be able to get it from *xsetwacom list* also.

By inverted I mean the screen rotated 180 degress instead of right or left portrait.  There is a bug in xf86-input-wacom-0.10.10 where cw and ccw are swapped so that's why stylus and touch are off in the Portrait orientations.  So if you want Portrait you'll have to update your xf86-input-wacom.

---

### Post by limotux on 2011-09-01
```
limo@lmde ~ $ xsetwacom set "device name" Gesture on
Cannot find device 'device name'.
limo@lmde ~ $ 

```In potrait there is 90 degrees difference in direction, in landscape 180 degrees.

Regarding xf86-input-wacom , wher can I get the latest?

p.s: here [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom) , but I won't do anything till you tell me what to do.

p.p.s.
> 
limo@lmde ~ $ xsetwacom list 
Serial Wacom Tablet eraser          id: 17    type: ERASER    
Serial Wacom Tablet touch           id: 18    type: TOUCH     
Serial Wacom Tablet stylus          id: 19    type: STYLUS    
limo@lmde ~ $ 


---

### Post by Favux on 2011-09-01
You need to find the device name.  It's probably *Wacom Serial Tablet touch*.  So what is the output in a terminal of?
```
xsetwacom list
```
Yes, that link is correct.  You need to update to at least 0.11.1 I believe.  The Bamboo P&T HOW TO we used before has Ubuntu libraries and Debian uses different names for them.  So if you need libraries to compile you'll have to figure out what the names are.

---

### Post by limotux on 2011-09-01
now running:
```
git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom
``` and result:
```
limo@lmde ~ $ git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom
Cloning into xf86-input-wacom...
remote: Counting objects: 10686, done.
remote: Compressing objects: 100% (5189/5189), done.
remote: Total 10686 (delta 8301), reused 6914 (delta 5482)
Receiving objects: 100% (10686/10686), 2.75 MiB | 44 KiB/s, done.
Resolving deltas: 100% (8301/8301), done.

```

What next?

---

### Post by Favux on 2011-09-01
Does:
```
xsetwacom set "Serial Wacom Tablet touch" Gesture on
```
turn multi-touch on?

```
cd xf86-input-wacom

./autogen.sh --prefix=/usr

make

sudo make install
```
I don't know if you need to tell it 64 bit with Debian Mint.  Does it have sudo?

---

### Post by limotux on 2011-09-01
thanks for your patience.
I'll try the above later. I have to go now.
Sorry.

---

### Post by limotux on 2011-09-02
> **Favux said:**
> Does:
```
xsetwacom set "Serial Wacom Tablet touch" Gesture on
```turn multi-touch on?

```
cd xf86-input-wacom

./autogen.sh --prefix=/usr

make

sudo make install
```I don't know if you need to tell it 64 bit with Debian Mint.  Does it have sudo?

```
limo@lmde ~ $ xsetwacom set "Serial Wacom Tablet touch" Gesture on
limo@lmde ~ $ cd xf86-input-wacom
limo@lmde ~/xf86-input-wacom $ ./autogen.sh --prefix=/usr
./autogen.sh: 9: ./autogen.sh: autoreconf: not found
limo@lmde ~/xf86-input-wacom $ 


```To answer your questions:
- Yes, now multitouch works. (after rebooting it didn't work, had to do (xsetwacom set "Serial Wacom Tablet touch" Gesture on) again
- I'm on 32 bit
- Yes, sudo works. (LMDE, Gnome, 32 bit, uses debian testing repos, it's a rolling release)

---

### Post by Favux on 2011-09-02
Good.  Just set up the xsetwacom command in a script to autostart like in Part IV. of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  xsetwacom commands are run time commands and won't last through a restart otherwise.

The line:
```
./autogen.sh: 9: ./autogen.sh: autoreconf: not found

```
is telling you that you are missing the autoconf library.

Remember the library/dependency line (for Ubuntu) on the BambooPT HOW TO is:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libxinerama-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev

```
Hopefully you won't need all of these.  For autoconf you probably need something like:
```
sudo apt-get install autoconf
```
using whatever the name Debian uses for autoconf.  Which you can get from google or looking at available Debian (& Mint?) packages.  And you'll have to do the same kind of thing if other errors are thrown up.

---

### Post by limotux on 2011-09-02
```
limo@lmde ~ $ sudo apt-get install autoconf
[sudo] password for limo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libedata-cal1.2-10 libedata-book1.2-8
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  automake
Suggested packages:
  autoconf2.13 autoconf-archive gnu-standards autoconf-doc libtool
The following NEW packages will be installed:
  autoconf automake
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 1,415 kB of archives.
After this operation, 4,178 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ftp.debian.org/debian/ testing/main autoconf all 2.68-1 [804 kB]
Get:2 http://ftp.debian.org/debian/ testing/main automake all 1:1.11.1-1 [611 kB]
Fetched 1,415 kB in 28s (49.7 kB/s)                                            
Selecting previously deselected package autoconf.
(Reading database ... 183292 files and directories currently installed.)
Unpacking autoconf (from .../autoconf_2.68-1_all.deb) ...
Selecting previously deselected package automake.
Unpacking automake (from .../automake_1%3a1.11.1-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up autoconf (2.68-1) ...
Setting up automake (1:1.11.1-1) ...
update-alternatives: using /usr/bin/automake-1.11 to provide /usr/bin/automake (automake) in auto mode.
N: Ignoring file 'dropbox.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'dropbox.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'dropbox.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
limo@lmde ~ $ 

```

This dropbox error is a bit funny, what do you think is the situation now? what next?
I believe I have what's necessary to compile and create a .deb, as I have compiled fjbtndrv from source.

---

### Post by Favux on 2011-09-02
Alright, when you installed autoconf it required another library which was a dependency, namely automake.  So now you have autoconf and automake on your system.

So now your repeat the compile starting with:
```
./autogen.sh --prefix=/usr

```
in the xf86-input-wacom folder.  And see if it it goes through or throws up another error and asks for another library.

By the way from *Xorg -version*:
```
Build Operating System: Linux 2.6.32-5-amd64 i686 Debian

```
you see amd64 which seems to be saying you have a 64-bit install.  Are you sure it is a 32-bit?  Maybe that's just saying the 32-bit kernel was built on a 64-bit kernel system.

From that you have:
kernel:  3.0.0-1-686-pae  (the pae extension is consistent with 32-bit.  It allows the system to address RAM memory beyond the old 2 GB limit of 32-bit systems.)

X.Org X Server:  1.10.4

---

### Post by limotux on 2011-09-02
[CODElimo@lmde ~ $ cd xf86-input-wacom
limo@lmde ~/xf86-input-wacom $ ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:43: error: **must install xorg-macros** 1.8 or later before running autoconf/autogen
configure.ac:43: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: /usr/bin/autom4te failed with exit status: 1
autoreconf: aclocal failed with exit status: 1
limo@lmde ~/xf86-input-wacom $ 
][/CODE]

So, in synaptic I searched for **xorg-macros**, the search resulted in one package called "xutils-dev". Should I install it?

And yes, I'm sure it's 32 bit(simply I never use 32 bit, the same cd/dvd is installed in virtualbox which I beleive impossible to run 64 bit, and yes I have 8 GB Ram, and I beleive it is accessed through the pae kernel, my processor is intel for sure not AMD, specs here [http://computershopper.com/laptops/reviews/fujitsu-lifebook-t4310](http://computershopper.com/laptops/reviews/fujitsu-lifebook-t4310) )

---

### Post by Favux on 2011-09-02
Yes, exactly.  Nice work.  Notice it's also in the Ubuntu library line.

So you are assembling the Debian Mint equivalent.

---

### Post by limotux on 2011-09-02
Installed "xutils-dev" from synaptic , then

```
limo@lmde ~/xf86-input-wacom $ ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.ac:39: error: possibly undefined macro: AC_DISABLE_STATIC
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:40: error: possibly undefined macro: AC_PROG_LIBTOOL
autoreconf: /usr/bin/autoconf failed with exit status: 1
limo@lmde ~/xf86-input-wacom $ 
```I notice some errors!

---

### Post by Favux on 2011-09-02
Good, you're picking it up.  It now looks like it is asking you to install the *libtool* library or library tool.

---

### Post by limotux on 2011-09-02
ok.. installed "libtool"

then

```
limo@lmde ~ $ cd xf86-input-wacom
limo@lmde ~/xf86-input-wacom $ ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
configure.ac:40: installing `./config.guess'
configure.ac:40: installing `./config.sub'
configure.ac:34: installing `./install-sh'
configure.ac:34: installing `./missing'
src/Makefile.am: installing `./depcomp'
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
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
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc option to accept ISO C99... -std=gnu99
checking whether __clang__ is declared... no
checking whether __INTEL_COMPILER is declared... no
checking whether __SUNPRO_C is declared... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking if gcc -std=gnu99 supports -Werror=attributes... no
checking for doxygen... no
configure: WARNING: doxygen not found - documentation targets will be skipped
checking for rint in -lm... yes
checking for XORG... no
configure: error: Package requirements (xorg-server >= 1.7.0 xproto xext kbproto inputproto randrproto) were not met:

No package 'xorg-server' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
limo@lmde ~/xf86-input-wacom $ 
```

I'm afraid of the unfamous "dependency hell":confused:

what next?

---

### Post by Favux on 2011-09-02
At a guess it is asking for x11proto-input-dev and/or xserver-xorg-dev.

---

### Post by limotux on 2011-09-03
ok, ```
Installed the following packages:
libpciaccess-dev (0.12.1-1)
libxkbfile-dev (1:1.0.7-1)
x11proto-dri2-dev (2.6-2)
x11proto-fonts-dev (2.1.1-1)
x11proto-video-dev (2.3.1-1)
xserver-xorg-dev (2:1.10.4-1)

```then

```
limo@lmde ~ $ cd xf86-input-wacom
limo@lmde ~/xf86-input-wacom $ ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
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
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc option to accept ISO C99... -std=gnu99
checking whether __clang__ is declared... no
checking whether __INTEL_COMPILER is declared... no
checking whether __SUNPRO_C is declared... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking if gcc -std=gnu99 supports -Werror=attributes... no
checking for doxygen... no
configure: WARNING: doxygen not found - documentation targets will be skipped
checking for rint in -lm... yes
checking for XORG... yes
checking for X11... yes
checking for UDEV... no
configure: error: Package requirements (libudev) were not met:

No package 'libudev' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables UDEV_CFLAGS
and UDEV_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
limo@lmde ~/xf86-input-wacom $
```I'm afraid I'm trapped in the dependency hell,  I don't know why I have a gut fealing that "./autogen.sh --prefix=/usr" should be done as root. what you think?

All what is needed is to get the touch and stylus move the cursor in the correct direction, I remember we did it before in the old thread by editing a file and changing some values... 

Just trying to understand why do we need to install all this stuff?

---

### Post by Favux on 2011-09-03
Now it is asking for *libudev-dev*.  What I've noticed is that Debian Mint seems to be using the same library names as Ubuntu and not the Debian names.  It looks like to me you could just use the entire library/dependency line in post #13 and be done with it.  Have you tried that?  In other words it appears you could just follow the instructions in the Bamboo P&T HOW TO like you have done before.

We're updating your xf86-input-wacom, the Wacom X driver, to get the bug fix for portrait orientation like we talked about earlier.

---

### Post by limotux on 2011-09-03
You mean I should do the following:
```
sudo apt-get install autoconf
```I remember I did it with some errors,

Or should I do:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libxinerama-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev
```As you mentioned, AFAIK Ubuntu is based on debian (but not really the same, a .deb for Debian won't run on Ubuntu, and vice verca), but LMDE is strictly Debian, it even uses Debian Testing repos as pure Debian, moreover it is a bit tweaked or customized, but still the same. I don't know it this facilitates for you to help me.

Now, I'll appreciate your patience to tell me step by step as I don't want to take the risk of messing things up or installing unnecessary packages on this machine, it's the one I depend on for work.

---

### Post by Favux on 2011-09-03
That's why we're taking it a bit at a time.  I'm just surprised that the library names appear the same.  I recall differences when helping Debian users.  So what's wrong with trying the entire line (the second one) and seeing what happens?  If it throws up errors I assume that will be about libraries with different names.  Which is what you want to know anyway.

---

### Post by limotux on 2011-09-03
ok.. here is the result

```
limo@lmde ~ $ sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libxinerama-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev
[sudo] password for limo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
autoconf is already the newest version.
build-essential is already the newest version.
libtool is already the newest version.
libx11-dev is already the newest version.
libxi-dev is already the newest version.
libxinerama-dev is already the newest version.
libxrandr-dev is already the newest version.
pkg-config is already the newest version.
x11proto-input-dev is already the newest version.
xserver-xorg-dev is already the newest version.
xutils-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libedata-cal1.2-10 libedata-book1.2-8
Use 'apt-get autoremove' to remove them.
Suggested packages:
  ncurses-doc
The following NEW packages will be installed:
  libncurses5-dev libudev-dev
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 533 kB of archives.
After this operation, 1,761 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ftp.debian.org/debian/ testing/main libncurses5-dev i386 5.9-1 [467 kB]
Get:2 http://ftp.debian.org/debian/ testing/main libudev-dev i386 172-1 [65.6 kB]
Fetched 533 kB in 11s (45.6 kB/s)                                              
Selecting previously deselected package libncurses5-dev.
(Reading database ... 183984 files and directories currently installed.)
Unpacking libncurses5-dev (from .../libncurses5-dev_5.9-1_i386.deb) ...
Selecting previously deselected package libudev-dev.
Unpacking libudev-dev (from .../libudev-dev_172-1_i386.deb) ...
Setting up libncurses5-dev (5.9-1) ...
Setting up libudev-dev (172-1) ...
N: Ignoring file 'dropbox.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'dropbox.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'dropbox.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
limo@lmde ~ $ 

```As far as I understand this is success, and believe the errors at the end are related to dropbox, I've seen it before but I don't remember the situation, but I remember it didn't affect what I was doing.

So, my personal understanding - and I may be wrong - I can consider the command done without errors. Do you agree with me?

---

### Post by Favux on 2011-09-03
Yes, it looks that way to me.  Go ahead and try to do the compile now.  Hopefully no more errors.

---

### Post by limotux on 2011-09-03
that seems to me ok

```
limo@lmde ~ $ cd xf86-input-wacom
limo@lmde ~/xf86-input-wacom $ ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
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
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc option to accept ISO C99... -std=gnu99
checking whether __clang__ is declared... no
checking whether __INTEL_COMPILER is declared... no
checking whether __SUNPRO_C is declared... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking if gcc -std=gnu99 supports -Werror=attributes... no
checking for doxygen... no
configure: WARNING: doxygen not found - documentation targets will be skipped
checking for rint in -lm... yes
checking for XORG... yes
checking for X11... yes
checking for UDEV... yes
checking whether the linker supports -wrap... yes
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
config.status: executing depfiles commands
config.status: executing libtool commands
limo@lmde ~/xf86-input-wacom $ 

```

I feel we'll celebrate in a few minutes.

---

### Post by Favux on 2011-09-03
Looks good.  Have you done the:
```
make

sudo make install
```
yet and rebooted?

---

### Post by limotux on 2011-09-03
```
limo@lmde ~/xf86-input-wacom $ make
make  all-recursive
make[1]: Entering directory `/home/limo/xf86-input-wacom'
Making all in conf
make[2]: Entering directory `/home/limo/xf86-input-wacom/conf'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/conf'
Making all in doc
make[2]: Entering directory `/home/limo/xf86-input-wacom/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/doc'
Making all in src
make[2]: Entering directory `/home/limo/xf86-input-wacom/src'
  CC     xf86Wacom.lo
  CC     wcmCommon.lo
  CC     wcmConfig.lo
  CC     wcmISDV4.lo
../src/wcmISDV4.c: In function 'model_from_sysfs':
../src/wcmISDV4.c:980:2: warning: format not a string literal, argument types not checked [-Wformat-nonliteral]
../src/wcmISDV4.c: In function 'isdv4ProbeKeys':
../src/wcmISDV4.c:1021:2: warning: format not a string literal, argument types not checked [-Wformat-nonliteral]
  CC     wcmFilter.lo
  CC     wcmUSB.lo
  CC     wcmXCommand.lo
  CC     wcmValidateDevice.lo
  CC     wcmTouchFilter.lo
  CCLD   wacom_drv.la
make[2]: Leaving directory `/home/limo/xf86-input-wacom/src'
Making all in man
make[2]: Entering directory `/home/limo/xf86-input-wacom/man'
  GEN    wacom.4
  GEN    xsetwacom.1
make[2]: Leaving directory `/home/limo/xf86-input-wacom/man'
Making all in include
make[2]: Entering directory `/home/limo/xf86-input-wacom/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/include'
Making all in tools
make[2]: Entering directory `/home/limo/xf86-input-wacom/tools'
  CC     xsetwacom.o
  CCLD   xsetwacom
  CC     isdv4-serial-debugger.o
  CCLD   isdv4-serial-debugger
make[2]: Leaving directory `/home/limo/xf86-input-wacom/tools'
Making all in test
make[2]: Entering directory `/home/limo/xf86-input-wacom/test'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/test'
make[2]: Entering directory `/home/limo/xf86-input-wacom'
make[2]: Leaving directory `/home/limo/xf86-input-wacom'
make[1]: Leaving directory `/home/limo/xf86-input-wacom'
limo@lmde ~/xf86-input-wacom $ sudo make install
[sudo] password for limo: 
``````
limo@lmde ~/xf86-input-wacom $ sudo make install
[sudo] password for limo: 
Sorry, try again.
[sudo] password for limo: 
Making install in conf
make[1]: Entering directory `/home/limo/xf86-input-wacom/conf'
make[2]: Entering directory `/home/limo/xf86-input-wacom/conf'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/X11/xorg.conf.d" || /bin/mkdir -p "/usr/share/X11/xorg.conf.d"
 /usr/bin/install -c -m 644 50-wacom.conf '/usr/share/X11/xorg.conf.d'
test -z "" || /bin/mkdir -p ""
make[2]: Leaving directory `/home/limo/xf86-input-wacom/conf'
make[1]: Leaving directory `/home/limo/xf86-input-wacom/conf'
Making install in doc
make[1]: Entering directory `/home/limo/xf86-input-wacom/doc'
make[2]: Entering directory `/home/limo/xf86-input-wacom/doc'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/doc'
make[1]: Leaving directory `/home/limo/xf86-input-wacom/doc'
Making install in src
make[1]: Entering directory `/home/limo/xf86-input-wacom/src'
make[2]: Entering directory `/home/limo/xf86-input-wacom/src'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/xorg/modules/input" || /bin/mkdir -p "/usr/lib/xorg/modules/input"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   wacom_drv.la '/usr/lib/xorg/modules/input'
libtool: install: /usr/bin/install -c .libs/wacom_drv.so /usr/lib/xorg/modules/input/wacom_drv.so
libtool: install: /usr/bin/install -c .libs/wacom_drv.lai /usr/lib/xorg/modules/input/wacom_drv.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/lib/xorg/modules/input
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/xorg/modules/input

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Leaving directory `/home/limo/xf86-input-wacom/src'
make[1]: Leaving directory `/home/limo/xf86-input-wacom/src'
Making install in man
make[1]: Entering directory `/home/limo/xf86-input-wacom/man'
make[2]: Entering directory `/home/limo/xf86-input-wacom/man'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/man/man4" || /bin/mkdir -p "/usr/share/man/man4"
 /usr/bin/install -c -m 644 wacom.4 '/usr/share/man/man4'
test -z "/usr/share/man/man1" || /bin/mkdir -p "/usr/share/man/man1"
 /usr/bin/install -c -m 644 xsetwacom.1 '/usr/share/man/man1'
make[2]: Leaving directory `/home/limo/xf86-input-wacom/man'
make[1]: Leaving directory `/home/limo/xf86-input-wacom/man'
Making install in include
make[1]: Entering directory `/home/limo/xf86-input-wacom/include'
make[2]: Entering directory `/home/limo/xf86-input-wacom/include'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/include/xorg" || /bin/mkdir -p "/usr/include/xorg"
 /usr/bin/install -c -m 644 Xwacom.h wacom-properties.h isdv4.h '/usr/include/xorg'
make[2]: Leaving directory `/home/limo/xf86-input-wacom/include'
make[1]: Leaving directory `/home/limo/xf86-input-wacom/include'
Making install in tools
make[1]: Entering directory `/home/limo/xf86-input-wacom/tools'
make[2]: Entering directory `/home/limo/xf86-input-wacom/tools'
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c xsetwacom isdv4-serial-debugger '/usr/bin'
libtool: install: /usr/bin/install -c xsetwacom /usr/bin/xsetwacom
libtool: install: /usr/bin/install -c isdv4-serial-debugger /usr/bin/isdv4-serial-debugger
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/tools'
make[1]: Leaving directory `/home/limo/xf86-input-wacom/tools'
Making install in test
make[1]: Entering directory `/home/limo/xf86-input-wacom/test'
make[2]: Entering directory `/home/limo/xf86-input-wacom/test'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/test'
make[1]: Leaving directory `/home/limo/xf86-input-wacom/test'
make[1]: Entering directory `/home/limo/xf86-input-wacom'
make[2]: Entering directory `/home/limo/xf86-input-wacom'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/pkgconfig" || /bin/mkdir -p "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 xorg-wacom.pc '/usr/lib/pkgconfig'
make[2]: Leaving directory `/home/limo/xf86-input-wacom'
make[1]: Leaving directory `/home/limo/xf86-input-wacom'
limo@lmde ~/xf86-input-wacom $ 
```
Will reboot and test tablet and cursor movements. Just a minute

---

### Post by limotux on 2011-09-03
Ok, rebooted.
But still cursor with touch does not rotate with screen, i.e.:
On first rotation which is portrait mode, I move up it moves right, moving right moves down

---

### Post by Favux on 2011-09-03
Alright.  We fixed the portrait problem and there appears to be another one because now it is 90 degrees out of phase.  That would indicate that the fjbtndrv rotation script isn't working for the Wacom input tools i.e. stylus, touch and eraser.  I can't remember where it installs the script.  Do you know?

---

### Post by limotux on 2011-09-03
'/home/limo/fjbtndrv-2.2.1' is this the one you are asking about?

It's the folder created upon compiling fjbtndrv

By the way, during booting it shows a message that fjbtndrv started and it actually rotates automatically.

What file do you want to edit?

---

### Post by Favux on 2011-09-03
It puts files elsewhere in some directory.  It's the directory I need to remember.  I'll have to see if I can recall or have notes or whatever so I can track it down.  Then we can look at your rotation script and see if there is a problem.

---

### Post by limotux on 2011-09-03
what file you need?
is it here [http://ubuntuforums.org/showthread.php?t=1597047&page=8](http://ubuntuforums.org/showthread.php?t=1597047&page=8)

( **rotate-wacom.sh** located at /usr/lib/fjbtndrv)

---

### Post by Favux on 2011-09-03
Great, nice job!  Yes the rotate-wacom.sh located at /usr/lib/fjbtndrv is what I was thinking of.  Have you tried the change jruh64 made?

---

### Post by limotux on 2011-09-03
hmmm...
tried to change n, r, l, i to the order   r, i, l, n
```

#!/bin/sh

test "$ACTION" = "rotated" || exit 0

case "$ORIENTATION" in
   [B] n*) val=0 ;;
    r*) val=1 ;;
    l*) val=2 ;;
    i*) val=3 ;;[/B]
    *)  exit 1 ;;
esac

# xinput installed?
xinput --version || exit 0

export LC_ALL=C

xinput list --short \
| sed 's/^[^[:alnum:]]* \(.*\) *id=.*/\1/p; d' \
| grep -vi 'virtual' \
| while read dev; do
    if xinput list-props "$dev" | grep -q 'Wacom Rotation'; then
        xinput set-prop "$dev" 'Wacom Rotation' $val
    fi
done

exit 0

```and rebooted

no difference happened.

returned it to it's original state (above) by copying from desktop.

Now, even after rebooting tablet does not rotate the screen nor the buttons as before. :(

I revised what I did, would

```
. rotate-wacom.sh
``` issued by mistake cause this?

Sorry, I hope I'm not making your life harder.

Please help.

---

### Post by Favux on 2011-09-03
Hmmm it could.  With a directory or a shell command you can't have illegal characters and a space would be illegal.  The gui or Desktop hides that because it can handle that kind of thing.

So make sure it has the correct name.

Also I think you can use the original script.  I think the change he had to make was because of the bug, and now you've fixed the bug.

---

### Post by limotux on 2011-09-04
something I don't understand here.

I recopied the original file and it is there
```
limo@lmde ~ $ cd /usr/lib/fjbtndrv
limo@lmde /usr/lib/fjbtndrv $ ls
rotate-wacom.sh  rotate-wacom.sh.save  switch-vkeyboard.sh
limo@lmde /usr/lib/fjbtndrv $ 
```I also repeated the autogen, make, sudo make instal
```
limo@lmde ~ $ cd xf86-input-wacom
limo@lmde ~/xf86-input-wacom $ ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
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
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc option to accept ISO C99... -std=gnu99
checking whether __clang__ is declared... no
checking whether __INTEL_COMPILER is declared... no
checking whether __SUNPRO_C is declared... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking if gcc -std=gnu99 supports -Werror=attributes... no
checking for doxygen... no
configure: WARNING: doxygen not found - documentation targets will be skipped
checking for rint in -lm... yes
checking for XORG... yes
checking for X11... yes
checking for UDEV... yes
checking whether the linker supports -wrap... yes
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
limo@lmde ~/xf86-input-wacom $ make
make  all-recursive
make[1]: Entering directory `/home/limo/xf86-input-wacom'
Making all in conf
make[2]: Entering directory `/home/limo/xf86-input-wacom/conf'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/conf'
Making all in doc
make[2]: Entering directory `/home/limo/xf86-input-wacom/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/doc'
Making all in src
make[2]: Entering directory `/home/limo/xf86-input-wacom/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/src'
Making all in man
make[2]: Entering directory `/home/limo/xf86-input-wacom/man'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/man'
Making all in include
make[2]: Entering directory `/home/limo/xf86-input-wacom/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/include'
Making all in tools
make[2]: Entering directory `/home/limo/xf86-input-wacom/tools'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/tools'
Making all in test
make[2]: Entering directory `/home/limo/xf86-input-wacom/test'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/test'
make[2]: Entering directory `/home/limo/xf86-input-wacom'
make[2]: Leaving directory `/home/limo/xf86-input-wacom'
make[1]: Leaving directory `/home/limo/xf86-input-wacom'
limo@lmde ~/xf86-input-wacom $ sudo make install
[sudo] password for limo: 
Making install in conf
make[1]: Entering directory `/home/limo/xf86-input-wacom/conf'
make[2]: Entering directory `/home/limo/xf86-input-wacom/conf'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/X11/xorg.conf.d" || /bin/mkdir -p "/usr/share/X11/xorg.conf.d"
 /usr/bin/install -c -m 644 50-wacom.conf '/usr/share/X11/xorg.conf.d'
test -z "" || /bin/mkdir -p ""
make[2]: Leaving directory `/home/limo/xf86-input-wacom/conf'
make[1]: Leaving directory `/home/limo/xf86-input-wacom/conf'
Making install in doc
make[1]: Entering directory `/home/limo/xf86-input-wacom/doc'
make[2]: Entering directory `/home/limo/xf86-input-wacom/doc'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/doc'
make[1]: Leaving directory `/home/limo/xf86-input-wacom/doc'
Making install in src
make[1]: Entering directory `/home/limo/xf86-input-wacom/src'
make[2]: Entering directory `/home/limo/xf86-input-wacom/src'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/xorg/modules/input" || /bin/mkdir -p "/usr/lib/xorg/modules/input"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   wacom_drv.la '/usr/lib/xorg/modules/input'
libtool: install: /usr/bin/install -c .libs/wacom_drv.so /usr/lib/xorg/modules/input/wacom_drv.so
libtool: install: /usr/bin/install -c .libs/wacom_drv.lai /usr/lib/xorg/modules/input/wacom_drv.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/sbin" ldconfig -n /usr/lib/xorg/modules/input
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/xorg/modules/input

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Leaving directory `/home/limo/xf86-input-wacom/src'
make[1]: Leaving directory `/home/limo/xf86-input-wacom/src'
Making install in man
make[1]: Entering directory `/home/limo/xf86-input-wacom/man'
make[2]: Entering directory `/home/limo/xf86-input-wacom/man'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/man/man4" || /bin/mkdir -p "/usr/share/man/man4"
 /usr/bin/install -c -m 644 wacom.4 '/usr/share/man/man4'
test -z "/usr/share/man/man1" || /bin/mkdir -p "/usr/share/man/man1"
 /usr/bin/install -c -m 644 xsetwacom.1 '/usr/share/man/man1'
make[2]: Leaving directory `/home/limo/xf86-input-wacom/man'
make[1]: Leaving directory `/home/limo/xf86-input-wacom/man'
Making install in include
make[1]: Entering directory `/home/limo/xf86-input-wacom/include'
make[2]: Entering directory `/home/limo/xf86-input-wacom/include'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/include/xorg" || /bin/mkdir -p "/usr/include/xorg"
 /usr/bin/install -c -m 644 Xwacom.h wacom-properties.h isdv4.h '/usr/include/xorg'
make[2]: Leaving directory `/home/limo/xf86-input-wacom/include'
make[1]: Leaving directory `/home/limo/xf86-input-wacom/include'
Making install in tools
make[1]: Entering directory `/home/limo/xf86-input-wacom/tools'
make[2]: Entering directory `/home/limo/xf86-input-wacom/tools'
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c xsetwacom isdv4-serial-debugger '/usr/bin'
libtool: install: /usr/bin/install -c xsetwacom /usr/bin/xsetwacom
libtool: install: /usr/bin/install -c isdv4-serial-debugger /usr/bin/isdv4-serial-debugger
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/tools'
make[1]: Leaving directory `/home/limo/xf86-input-wacom/tools'
Making install in test
make[1]: Entering directory `/home/limo/xf86-input-wacom/test'
make[2]: Entering directory `/home/limo/xf86-input-wacom/test'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/limo/xf86-input-wacom/test'
make[1]: Leaving directory `/home/limo/xf86-input-wacom/test'
make[1]: Entering directory `/home/limo/xf86-input-wacom'
make[2]: Entering directory `/home/limo/xf86-input-wacom'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/pkgconfig" || /bin/mkdir -p "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 xorg-wacom.pc '/usr/lib/pkgconfig'
make[2]: Leaving directory `/home/limo/xf86-input-wacom'
make[1]: Leaving directory `/home/limo/xf86-input-wacom'
limo@lmde ~/xf86-input-wacom $ 

```Still no rotation, no buttons though it was working before.

and here is the file in the folder
```
  

#!/bin/sh

test "$ACTION" = "rotated" || exit 0

case "$ORIENTATION" in
    n*) val=0 ;;
    r*) val=1 ;;
    l*) val=2 ;;
    i*) val=3 ;;
    *)  exit 1 ;;
esac

# xinput installed?
xinput --version || exit 0

export LC_ALL=C

xinput list --short \
| sed 's/^[^[:alnum:]]* \(.*\) *id=.*/\1/p; d' \
| grep -vi 'virtual' \
| while read dev; do
    if xinput list-props "$dev" | grep -q 'Wacom Rotation'; then
        xinput set-prop "$dev" 'Wacom Rotation' $val
    fi
done

exit 0


```what you think? would I need to reinstal fjbtndrv an other debs created when compiled?

---

### Post by limotux on 2011-10-06
Well, sorry favux for giving you hard time. I really appreciate your support.

I really don't know what caused it not to work.

Finally, I removed everything, and reinstaled fjbtndrv. Now the screan rotates when I fold the screen, and some buttons working and rotate the screen as well.

I hope you can help me at least with fixing the direction of touch and stylus.

I don't want to start trying on my own so it will be eaier for you.

Thank you for your help and patience.

---

### Post by limotux on 2011-10-06
p.s.:
I have now  **rotate-wacom.sh** located at /usr/lib/fjbtndrv
 and it is as follows:

```
#!/bin/sh

test "$ACTION" = "rotated" || exit 0

case "$ORIENTATION" in
    n*) val=0 ;;
    r*) val=1 ;;
    l*) val=2 ;;
    i*) val=3 ;;
    *)  exit 1 ;;
esac

# xinput installed?
xinput --version || exit 0

export LC_ALL=C

xinput list --short \
| sed 's/^[^[:alnum:]]* \(.*\) *id=.*/\1/p; d' \
| grep -vi 'virtual' \
| while read dev; do
    if xinput list-props "$dev" | grep -q 'Wacom Rotation'; then
        xinput set-prop "$dev" 'Wacom Rotation' $val
    fi
done

exit 0
```

what is your advice?

---

### Post by limotux on 2011-10-06
p.s:

As mentioned in our first thread [http://ubuntuforums.org/showthread.php?t=1597047&page=8](http://ubuntuforums.org/showthread.php?t=1597047&page=8)

I did:
```
limo@lmde ~/xf86-input-wacom $ xrandr -o left 
limo@lmde ~/xf86-input-wacom $ xsetwacom set "Serial Wacom Tablet stylus" rotate CW
limo@lmde ~/xf86-input-wacom $ 

```

and it seems to correct touch and stylus directions after getting the second portrait mode

This seems to be the solution, but not sure which files to edit or what to change in it.

I'll be waiting for your feed back.

---

### Post by Favux on 2011-10-06
Hi limotux,

Could you remind me what Distro and release you are using now?  Do you still have a more recent xf86-input-wacom, one that fixes the CW and CCW swap?  In other words xf86-input-wacom-0.11.1 or more recent (git clone).

Alright if right and left portrait orientations are reversed all you should have to do is make the following changes on your fjbtndrv rotation script.  Instead of:
```
case "$ORIENTATION" in
    n*) val=0 ;;
    r*) val=1 ;;
    l*) val=2 ;;
    i*) val=3 ;;
    *)  exit 1 ;;
esac

```
Change it to:
```
case "$ORIENTATION" in
    n*) val=0 ;;
    r*) val=2 ;;
    l*) val=1 ;;
    i*) val=3 ;;
    *)  exit 1 ;;
esac

```
You can use:
```
gksudo gedit /usr/lib/fjbtndrv/rotate-wacom.sh
```

---

### Post by limotux on 2011-10-06
> **Favux said:**
> Hi limotux,

Could you remind me what Distro and release you are using now? [SIZE=3][COLOR=Blue]***(I'm still on LMDE updated)***[/COLOR][/SIZE] Do you still have a more recent xf86-input-wacom, [SIZE=3][COLOR=Blue]**(I'm not sure how to tell, but I believe it's the same as before, but I can say I have xserver-xorg-input-wacom 0.10.10+20110203-1+b2, and the same previous fjbtndrv I compiled previously)**[/COLOR][/SIZE] one that fixes the CW and CCW swap?  In other words xf86-input-wacom-0.11.1 or more recent (git clone).

Alright if right and left portrait orientations are reversed all you should have to do is make the following changes on your fjbtndrv rotation script.  Instead of:
```
case "$ORIENTATION" in
    n*) val=0 ;;
    r*) val=1 ;;
    l*) val=2 ;;
    i*) val=3 ;;
    *)  exit 1 ;;
esac

```Change it to:
```
case "$ORIENTATION" in
    n*) val=0 ;;
    r*) val=2 ;;
    l*) val=1 ;;
    i*) val=3 ;;
    *)  exit 1 ;;
esac

```You can use:
```
gksudo gedit /usr/lib/fjbtndrv/rotate-wacom.sh
```

I changed rotate-wacom.sh as you said, rebooted, no change happens.
I beleive the solution is in my previous post:
```
limo@lmde ~/xf86-input-wacom $ xrandr -o left  
limo@lmde ~/xf86-input-wacom $ xsetwacom set "Serial Wacom Tablet stylus" rotate CW 
limo@lmde ~/xf86-input-wacom $
```
I did this as in our earlier thread with john, but I'm not sure if I'm correct or how to do it.:(

_**p.s. first press on tablet button or flipping screen to tablet mode gives me portrait, when I move up the cursor moves right.**_

---

### Post by Favux on 2011-10-06
Sorry, you're 90 degrees out of phase not 180 degrees so it is not a CW and CCW swap, the input tools aren't rotating.  If you go to inverted does the stylus move correctly or is it now 180 degrees out of phase?

When you rotate the tablet's screen to tablet mode is the screen orientation suppose to change automatically or are you suppose to press a button on the screen's bezel to rotate the screen orientation and the Wacom input tools?

---

### Post by limotux on 2011-10-06
First portrait it adds 90 degrees, i.e.: moving finger up the cursor goes right, moving finger right the cursor goes down.
Second portrait it subtracts 90 degrees  i.e: moving finger up the cursor goes left, moving finger left the cursor goes down (seems really funny, I can't immagine an explanation)

In landscape, where the screen bottom displayed is at the physical bottom of the screen (the tool bar is at the hinge) it moves correct directions as in normal laptop mode, the second landscape there is a 180 degreas difference.

And yes, when I flip the screen it rotates automatically to the first portrait position.
Do you think there is something that should be installed? All what I did as far as I remember is uninstalling fjbtndrv and other .debs that were produced when i compiled it, removed the folder /usr/lib/fjbtndrv/ then reinstalled them again. Maybe I tried as well some of the steps we did at the begining of this thread, but not sure if it was successful.

this seems to be really chalenging and needs a real expert.

---

### Post by limotux on 2011-10-07
Waiting for your suggestions Favux.

I can figure out from the previous post that screen rotates but touch and stylus don't rotate... I'm sure you have a way to get them rotate first then fix their directions if needed.

OMG.. this seems so hard for me.

---

### Post by Favux on 2011-10-07
Alright, I guess the script is broken since it rotates the screen orientation but not the Wacom tools.  Let's see if we can figure out why.

What is the output of the following?
```
xinput --version
```
and
```
xinput list --short
```
and
```
ls /sys/devices/platform
```

---

### Post by limotux on 2011-10-07
```
limo@lmde ~ $ xinput --version
The program 'xinput' is currently not installed.  To run 'xinput' please ask your administrator to install the package 'xinput'
xinput: command not found
limo@lmde ~ $ 

```

```
limo@lmde ~ $ xinput list --short
The program 'xinput' is currently not installed.  To run 'xinput' please ask your administrator to install the package 'xinput'
xinput: command not found
limo@lmde ~ $ 

```

```
limo@lmde ~ $ ls /sys/devices/platform
alarmtimer  fsc_btns        i8042   power      regulatory.0  uevent
dock.0      fujitsu-laptop  pcspkr  reg-dummy  serial8250    vboxdrv.0
limo@lmde ~ $ 


```

---

### Post by Favux on 2011-10-07
Alright, I think Linux Mint uses apt-get.  Does the manual for it come up when you enter?
```
man apt-get
```

Also the output of:
```
ls /sys/devices/platform/fsc_btns
```
and
```
ls /sys/devices/platform/fujitsu-laptop
```

---

### Post by limotux on 2011-10-07
> **Favux said:**
> Alright, I think Linux Mint uses apt-get.  Does the manual for it come up when you enter?
```
man apt-get
```[I][COLOR=Blue]Yes it comes up
[/COLOR][/I]
Also the output of:
```
ls /sys/devices/platform/fsc_btns
``````
limo@lmde ~ $ ls /sys/devices/platform/fsc_btns
driver  input  modalias  power  subsystem  uevent
limo@lmde ~ $ 


```and
```
ls /sys/devices/platform/fujitsu-laptop
```

```
limo@lmde ~ $ ls /sys/devices/platform/fujitsu-laptop
brightness_changed  driver     lid             modalias  radios     uevent
dock                lcd_level  max_brightness  power     subsystem
limo@lmde ~ $ 


```

---

### Post by Favux on 2011-10-07
Alright, you don't have the xinput package installed which is why the script isn't working.  It is installed by default on Ubuntu.  So install it by entering in a terminal:
```
sudo apt-get install xinput
```
And now the rotation script should work.

Also I am curious about lid.  Is that open and close or for rotation?  In laptop mode when you enter:
```
cat /sys/devices/platform/fujitsu-laptop/lid
```
does it return say a 0?  And when you are in tablet mode does it return something different?  Say a 1?

---

### Post by limotux on 2011-10-08
ok... xinput installed. I can see it in package manager. I rebooted by the way after installing.
Here is what happened:
```
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libva-x11-1 liblog4j1.2-java-gcj libtar0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  xinput
0 upgraded, 1 newly installed, 0 to remove and 25 not upgraded.
Need to get 23.4 kB of archives.
After this operation, 90.1 kB of additional disk space will be used.
Get:1 http://ftp.debian.org/debian/ testing/main xinput i386 1.5.3-1 [23.4 kB]
Fetched 23.4 kB in 1s (12.5 kB/s) 
Selecting previously unselected package xinput.
(Reading database ... 189889 files and directories currently installed.)
Unpacking xinput (from .../xinput_1.5.3-1_i386.deb) ...
Processing triggers for man-db ...
Setting up xinput (1.5.3-1) ...
N: Ignoring file 'google-talkplugin.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-talkplugin.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'google-talkplugin.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
limo@lmde ~ $ 

```I think the last errors are meaningless.

I tried tablet mode after rebooting, still the same situation. :confused:

and about lid in normal mode and in tablet mode same result:
```
limo@lmde ~ $ cat /sys/devices/platform/fujitsu-laptop/lid
open
limo@lmde ~ $ 

```P.S. Mouse is moving properly in tablet mode as before, but stil touch and stylus have a problem.

---

### Post by Favux on 2011-10-08
Alright now with xinput installed the script still doesn't work.  So now repeat the two xinput commands I gave you a few posts earlier (they're what the script uses) and post the outputs.

So lid is *open* both in laptop and tablet mode?

---

### Post by limotux on 2011-10-08
> **Favux said:**
> Alright now with xinput installed the script still doesn't work.  So now repeat the two xinput commands I gave you a few posts earlier (they're what the script uses) and post the outputs.

```
[COLOR=Navy]limo@lmde ~ $ xinput --version
xinput version 1.5.3
XI version on server: 2.0
limo@lmde ~ $ [/COLOR]

[COLOR=Navy]limo@lmde ~ $ xinput list --short
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627;  USB OPTICAL MOUSE                          id=12    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=17    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=18    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=19    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                             id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=9    [slave  keyboard (3)]
    &#8627; Power Button                                id=10    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=11    [slave  keyboard (3)]
    &#8627; FJ Camera                                   id=13    [slave  keyboard (3)]
    &#8627; fsc tablet buttons                          id=14    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=15    [slave  keyboard (3)]
limo@lmde ~ $ [/COLOR]

[COLOR=Navy]limo@lmde ~ $ ls /sys/devices/platform
alarmtimer  fsc_btns        i8042   power      regulatory.0  uevent
dock.0      fujitsu-laptop  pcspkr  reg-dummy  serial8250    vboxdrv.0
limo@lmde ~ $ [/COLOR]




```So lid is *open* both in laptop and tablet mode?

yes.:(

---

### Post by Favux on 2011-10-08
So then it reads the devices in *virtual* and the final command it uses is:
```
xinput list-props "Serial Wacom Tablet stylus"
```
Post that output.  Then it pulls out the *Wacom Rotation* line.  So we want the command output in both laptop and rotated mode.  Say right portrait?  That will tell us if *Wacom Rotation* is changing values appropriately.

---

### Post by limotux on 2011-10-08
in normal mode:
```
limo@lmde ~ $ xinput list-props "Serial Wacom Tablet stylus"
Device 'Serial Wacom Tablet stylus':
    Device Enabled (131):    1
    Coordinate Transformation Matrix (133):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (249):    0
    Device Accel Constant Deceleration (250):    1.000000
    Device Accel Adaptive Deceleration (251):    1.000000
    Device Accel Velocity Scaling (252):    10.000000
    Device Node (273):    "/dev/ttyS0"
    Wacom Tablet Area (274):    0, 0, 26312, 16520
    Wacom Rotation (275):    0
    Wacom Pressurecurve (276):    0, 0, 100, 100
    Wacom Serial IDs (277):    227, 0, 2, 0
    Wacom Serial ID binding (278):    0
    Wacom Pressure Threshold (279):    27
    Wacom Sample and Suppress (280):    2, 4
    Wacom Enable Touch (281):    1
    Wacom Hover Click (282):    0
    Wacom Enable Touch Gesture (283):    1
    Wacom Touch Gesture Parameters (284):    50, 20, 250
    Wacom Tool Type (285):    "STYLUS" (266)
    Wacom Button Actions (286):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Device Product ID (287):    0, 227
    Wacom Debug Levels (288):    0, 0
limo@lmde ~ $ 

```in tablet mode (first portrait)
```
limo@lmde ~ $ xinput list-props "Serial Wacom Tablet stylus"
Device 'Serial Wacom Tablet stylus':
    Device Enabled (131):    1
    Coordinate Transformation Matrix (133):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (249):    0
    Device Accel Constant Deceleration (250):    1.000000
    Device Accel Adaptive Deceleration (251):    1.000000
    Device Accel Velocity Scaling (252):    10.000000
    Device Node (273):    "/dev/ttyS0"
    Wacom Tablet Area (274):    0, 0, 26312, 16520
    Wacom Rotation (275):    0
    Wacom Pressurecurve (276):    0, 0, 100, 100
    Wacom Serial IDs (277):    227, 0, 2, 0
    Wacom Serial ID binding (278):    0
    Wacom Pressure Threshold (279):    27
    Wacom Sample and Suppress (280):    2, 4
    Wacom Enable Touch (281):    1
    Wacom Hover Click (282):    0
    Wacom Enable Touch Gesture (283):    1
    Wacom Touch Gesture Parameters (284):    50, 20, 250
    Wacom Tool Type (285):    "STYLUS" (266)
    Wacom Button Actions (286):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Device Product ID (287):    0, 227
    Wacom Debug Levels (288):    0, 0
limo@lmde ~ $ 

```

---

### Post by Favux on 2011-10-08
Alright we're seeing with laptop or normal mode:
```
Wacom Rotation (275):    0

```
And in right portrait or cw mode:
```
Wacom Rotation (275):    0
```
I think then the script is suppose to use *xinput set-prop* to advance to the next value.  The numbers (val=) are at the beginning of the script.  Does this thing rotate through 360 degrees when it is working?  If not then it is expecting the Wacom Rotation value to change and it would be 1 in portrait.  I did a quick check and my value doesn't change when I change screen orientation.  I have to use the xsetwacom Rotate command and then the xinput value does change.

At least that's what it looks like at the quick read I'm giving it.  I'm not prepared to sit down and dissect the script.  I'm working on pushing out Magick Rotation 1.5 for the Oneiric release.

Why the xinput values aren't reflecting rotation, if they ever did the way I'm thinking, I don't know.  What you could do is go to the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") and try wacom rotate i.e. method 4.  See if it installs and works.  Or try a method 1 script in a launcher.  Just remove the screen rotate command so it only rotates the stylus and touch.

If we knew where the signal for the hinge switch that is triggering the screen orientation change was coming from we could try a different script.  I'm assuming there is a switch signal somewhere although it may not necessarily be in the hinge.  Reporting through ACPI?

---

### Post by limotux on 2011-10-08
I'm not sure I full understand your post, but I'll do my best!

> **Favux said:**
> Alright we're seeing with laptop or normal mode:
```
Wacom Rotation (275):    0

```And in right portrait or cw mode:
```
Wacom Rotation (275):    0
```I think then the script is suppose to use *xinput set-prop* to advance to the next value.  The numbers (val=) are at the beginning of the script. ** Does this thing rotate through 360 degrees when it is working?** ***[COLOR=Navy](I think so. Fliping the screen to tablet mode gives the first portrait mode, and I can rotate it wy clicking the button on the frame of the monitor)[/COLOR]***  If not then it is expecting the Wacom Rotation value to change and it would be 1 in portrait.  I did a quick check and my value doesn't change when I change screen orientation.  I have to use the xsetwacom Rotate command and then the xinput value does change.

At least that's what it looks like at the quick read I'm giving it.  I'm not prepared to sit down and dissect the script.  I'm working on pushing out Magick Rotation 1.5 for the Oneiric release.

Why the xinput values aren't reflecting rotation, if they ever did the way I'm thinking, I don't know.  What you could do is go to the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") and try wacom rotate i.e. method 4.  See if it installs and works.  Or try a method 1 script in a launcher.  Just remove the screen rotate command so it only rotates the stylus and touch.

If we knew where the signal for the hinge switch that is triggering the screen orientation change was coming from we could try a different script.  I'm assuming there is a switch signal somewhere although it may not necessarily be in the hinge.  Reporting through ACPI?

I hope my simple answer clarifies the situation a little bit.
As I said I'm not sure I fully understand the subject, so I prefere to wait for your instructions. I don't want to try something that makes it harder for you to help me.

I appreciate your patience and support. I know I'll never do it without your help.

p.s.: as in my previous post [http://ubuntuforums.org/showpost.php?p=11315353&postcount=42](http://ubuntuforums.org/showpost.php?p=11315353&postcount=42)

I tried
```
xrandr -o left 
```at terminal and it rotated the display to portrait mode

Then I did 
[CODExsetwacom set "Serial Wacom Tablet stylus" rotate CW][/CODE]
which made the touch and stylus work fine and move in the correct direction but in first portrait only. Further rotations by clicking the button makes it move in other directions

So, at the moment I can use my machine as a tablet any time by doing only
```
xsetwacom set "Serial Wacom Tablet stylus" rotate CW
```[COLOR=Red]This is correct and applies to first portrait only
[/COLOR]
[B]Then I think the question is:
How can I get this command to run and stay withe every boot instead of doing it manualy.
And how to issue other commands to rotate one step (90 degrees) more with every button press.[/B]

---

### Post by Favux on 2011-10-08
Let me try to summarize the situation as I see it.

You have two methods to rotate.
1) Hinge switch:  when you pivot and fold to a tablet a signal is sent.  That rotates the screen currently but not the stylus (or touch).  We don't know where that signal is or where the script that handles it is.  That's what we were trying to find.  The script has to be simple like the method 1 script example I show that goes to only right portrait and then back to laptop.

Since there appears to only be one rotation script in the fjbtndrv directory where you have the button assignments and what not it has to be somewhere else.  Once upon a time I saw a simple rotation script using an ACPI signal somewhere.  Ubuntu had installed it as a default for tablet PCs.  I think in the /etc directory somewhere.  I'm wondering if that is what is giving you your "automatic rotation".

2) Rotation button:  This rotates the screen through 360 degrees by 90 degree steps.  That is the script you posted.  And since the screen orientation rotates when you press the button we know the button binding to the rotation script is correct and working.


THE PROBLEM
Despite both methods/scripts rotating the screen they are not rotating the stylus/touch.  But we know your Wacom drivers are working because you are able to manually able to use a xsetwacom command to change the stylus and touch orientation.

So for some reason both of the scripts had their handling of xsetwacom commands broken at the same time.


THE SOLUTION
1) Install wacomrotate - if it works it will substitute for the two scripts busted handling of wacom tool rotation through xsetwacom.
2) Manually tell the tools to rotate.  But instead of entering each line (for stylus, eraser, touch) into a terminal each time set up a launcher for a xsetwacom script.  One script to rotate the tools to right portrait  the other to normal.  Or try to combine them like the method 1 script shows.  This means you essentially give up on your rotation button since it would be too cumbersome to handle, unless you want to try substituting the method 1 360 degree script for the one currently in the rotate-wacom.sh file.

---

### Post by Favux on 2011-10-08
Ha!  I found the "automatic" rotation script.  It is called rotatescreen.sh and is located in /etc/acpi.

Let's see if that is what your Fujitsu is using.  What is the output of:
```
cat /var/lib/acpi-support/screen-rotation
```
in laptop mode?  And when you are rotated to tablet?

---

### Post by limotux on 2011-10-08
```
limo@lmde ~ $ cat /var/lib/acpi-support/screen-rotation
cat: /var/lib/acpi-support/screen-rotation: No such file or directory
limo@lmde ~ $ 

```
No need of course to try it in tablet mode if it is not there!
and 
```
limo@lmde /etc/acpi $ ls
events  powerbtn-acpi-support.sh
limo@lmde /etc/acpi $ 

```

---

### Post by Favux on 2011-10-08
Shoot!  We could have fixed that.  Is it in the fjbtndrv directory then?  What does:
```
ls /usr/lib/fjbtndrv
```
show?

---

### Post by limotux on 2011-10-08
```
limo@lmde ~ $ ls /usr/lib/fjbtndrv
rotate-wacom.sh  switch-vkeyboard.sh
limo@lmde ~ $ 
```

---

### Post by Favux on 2011-10-08
What is the content of switch-vkeyboard.sh?  Please post it.

---

### Post by limotux on 2011-10-08
> **Favux said:**
> What is the content of switch-vkeyboard.sh?  Please post it.

at usr/lib/fjbtndrv

```
#!/bin/bash
# Sample script for fscd.
# Copy or link this script to rotate-normal and rotate-tablet.
#
# Copyright (C) 2008-2010 Robert Gerlach <khnz@users.sourceforge.net>
# 
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2.
################################################################################

oskb_bin=
[ "$oskb_bin" ] || oskb_bin="`type -p cellwriter`"
[ "$oskb_bin" ] || oskb_bin="`type -p onboard`"
[ "$oskb_bin" ] || oskb_bin="`type -p xvkbd`"
[ "$oskb_bin" ] || exit 0

case "$MODE" in

  tablet)
    if test "$ACTION" = "rotated"; then
      "$oskb_bin" &
    fi
    ;;

  normal)
    if test "$ACTION" = "rotating"; then
      pid=$( pgrep -u "$USER" "`basename "$oskb_bin"`" )
      if [ "$pid" ]; then
        kill -TERM $pid
      fi
    fi
    ;;

esac

exit 0
```

Out of curiosity. the virtuAL keyboard I have is florence, should I install any of the mentioned in the script above? (cellwriter, onboard, xvkbd)

---

### Post by Favux on 2011-10-08
Yes or add Florence to the script.

Finally a clue!  Apparently whatever the hinge switch signal is it is hooked to, at a guess, two scripts called *rotate-normal* and *rotate-tablet*.  You need to find those, tell me the directory they are in and post their contents.  That's ringing a dim bell in my memory.

---

### Post by limotux on 2011-10-08
searched using find from filesystem for both *rotate-normal* and [I]rotate-tablet, they are not found!
will install both virtual keyboards then remove perhaps one of them later along with florence perhaps
Edit: just installed xvkbd , onboard is not in my repos. I think it is enough for now.
[/I]

---

### Post by limotux on 2011-10-08
and here is the above .sh after adding florence

```

#!/bin/bash
# Sample script for fscd.
# Copy or link this script to rotate-normal and rotate-tablet.
#
# Copyright (C) 2008-2010 Robert Gerlach <khnz@users.sourceforge.net>
# 
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2.
################################################################################

oskb_bin=
[ "$oskb_bin" ] || oskb_bin="`type -p cellwriter`"
[ "$oskb_bin" ] || oskb_bin="`type -p onboard`"
[ "$oskb_bin" ] || oskb_bin="`type -p xvkbd`"
[ "$oskb_bin" ] || oskb_bin="`type -p florence`"
[ "$oskb_bin" ] || exit 0

case "$MODE" in

  tablet)
    if test "$ACTION" = "rotated"; then
      "$oskb_bin" &
    fi
    ;;

  normal)
    if test "$ACTION" = "rotating"; then
      pid=$( pgrep -u "$USER" "`basename "$oskb_bin"`" )
      if [ "$pid" ]; then
        kill -TERM $pid
      fi
    fi
    ;;

esac

exit 0

```

---

### Post by Favux on 2011-10-08
Nice work!

Maybe they are called *rotate-normal.sh* and *rotate-tablet.sh*?  Or those are sections of a script?  I think maybe where I saw that was in the other Fujitsu thread where I first found out where some of the fjbtndrv stuff was located.

---

### Post by limotux on 2011-10-08
the only .sh files that contain the word rotate is rotate-wacom.sh

why not think of your method that worked previously with me and John? The other thread i mean the one that is called something like wacom how to ( [http://ubuntuforums.org/showpost.php?p=6274392&postcount=1](http://ubuntuforums.org/showpost.php?p=6274392&postcount=1))

As far as I understand from your guide (method 4) I should install     wacomrotate_0.3.1_i386.deb from [http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/pool/main/w/wacomrotate/](http://ppa.launchpad.net/thjaeger/tabletpc/ubuntu/pool/main/w/wacomrotate/)

But not sure if these deb packages are ubuntu only or debian (lmde) or should I compile from source? (I think I should compile, right? please help me compile if so)

---

