---
title: "How can Iinstall GIMPShop"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by delphiexile on 2009-03-26
Hi everybody

I've downloaded GIMPShop from this URL:
[http://www.plasticbugs.com/blogimg/gimpshop-2.2.11.tar.bz2](http://www.plasticbugs.com/blogimg/gimpshop-2.2.11.tar.bz2)

I didn't know how to Install this kind of softwares , I think i saw a compilation process.

---

### Post by neu2buntu on 2009-03-26
right click on the tar.bz file and choose option "open with archive manager" then extract the file to say Desktop

(1) open the file on Desktop and look for "readme" or "install"

mostly you will find that you have to ./configure ,make and sudo make install by "cd" to the file through terminal.... i can help u with this ,just let us know the install instructions first

also give the exact name of the extracted file so you can copy and paste my commands to your terminal...ok

---

### Post by delphiexile on 2009-03-26
> **neu2buntu said:**
> right click on the tar.bz file and choose option "open with archive manager" then extract the file to say Desktop

(1) open the file on Desktop and look for "readme" or "install"

mostly you will find that you have to ./configure ,make and sudo make install by "cd" to the file through terminal.... i can help u with this ,just let us know the install instructions first


OK i'll try that now!!!

---

### Post by delphiexile on 2009-03-26
This solution doesn't work , but I've brought the INSTALL.txt file :

```


Installation instructions for GIMP 2.2
--------------------------------------

There are some basic steps to building and installing The GIMP.

GIMP 2.2 replaces GIMP 2.0. It is advised that you uninstall GIMP 2.0
before installing GIMP 2.2. If you want to keep GIMP 2.0 installed in
parallel to GIMP 2.2, you have to choose a separate prefix which is
not in your default library search path.

GIMP 2.2 is fully backward compatible to GIMP 2.0. Plug-ins and
scripts written for GIMP 2.0 will continue to work and don't need to
be changed nor recompiled to be used with GIMP 2.2.

The most important part is to make sure the requirements for a build
are fulfilled.  We depend on a number of tools and libraries which are
listed below. For libraries this means you need to also have the
header files installed.

  ******************************************************************
  * Unless you are experienced with building software from source, *
  * you should not attempt to build all these libraries yourself!  *
  * We suggest that you check if your distributor has development  *
  * packages of them and use these instead.                        *
  ******************************************************************

  1. You need to have installed a recent version of pkg-config available
     from http://www.freedesktop.org/software/pkgconfig/.  

  2. You need to have installed GTK+ version 2.4.4 or better. Do not
     try to use an older GTK+ version (1.2.x), it will not work.
     GTK+ itself needs recent versions of GLib (>= 2.4.5),
     Pango (>= 1.4.0) and ATK. Sources for these can be grabbed from
     ftp://ftp.gtk.org/. GTK+-2.x and friends can be installed side
     by side with GTK+-1.2.

  3. We require PangoFT2, a Pango backend that uses FreeType2. Make
     sure you have FreeType2 and fontconfig installed before you
     compile Pango.  FreeType2 can be downloaded from
     http://www.freetype.org/.  Fontconfig from
     http://freedesktop.org/fontconfig/.  GIMP 2.2 depends on
     freetype2 being newer than version 2.1.7. Older versions are
     known to have bugs that seriously affect stability of The GIMP.

  4. We use libart2. Grab the module libart_lgpl out of GNOME CVS or
     fetch the tarball from
     ftp://ftp.gnome.org/pub/gnome/sources/libart_lgpl/

  5. You may want to install other third party libraries or programs that
     are needed for some of the available plugins. We recommend to check
     that the following libraries are installed: libpng, libjpeg,
     libtiff, gimp-print (4.2.x), gtkhtml-2, libmng, librsvg, libwmf.

  6. Configure the GIMP by running the `configure' script. You may want
     to pass some options to it, see below.

  7. Build the GIMP by running `make'. The use of GNU make is recommened.
     If you need to tweak the build to make it work with other flavours
     of make, we'd appreciate if you'd send us a patch with the changes.

  8. Install the GIMP by running `make install'. In order to avoid clashes
     with other versions of The GIMP, we install a binary called gimp-2.2.
     By default there's also a link created so that you can type 'gimp'
     to start gimp-2.2. If you have the 2.0 version installed, you should
     still be able to run it using 'gimp-2.0'.

Please make sure you don't have any old GTK+-2.x, jpeg, etc. libraries 
lying around on your system, otherwise configure may fail to find the 
new ones.


Generic instructions for configuring and compiling auto-configured
packages are included below. Here is an illustration of commands that
might be used to build and install the GIMP. The actual configuration,
compilation and installation output is not shown.

  % tar xvfz gimp-2.2.x.tar.gz   # unpack the sources
  % cd gimp-2.2.x                # change to the toplevel directory
  % ./configure                  # run the `configure' script
  % make                         # build the GIMP
  % make install                 # install the GIMP


The `configure' script examines your system, and adapts the GIMP to
run on it. The script has many options, some of which are described in
the generic instructions included at the end of this file. All of the
options can be listed using the command `./configure --help'. There
are several special options the GIMP `configure' script recognizes.
These are:

  --enable-shared and --disable-shared.  This option affects whether
     shared libraries will be built or not. Shared libraries provide
     for much smaller executables. The default is to enable shared
     libraries. Disabling shared libraries is almost never a good idea.

  --enable-debug and --disable-debug.  This option causes the build
     process to compile with debugging enabled. If debugging is
     disabled, the GIMP will instead be compiled with optimizations turned
     on. The default is for debugging to be disabled. NOTE: This
     option is intended primarily as a convenience for developers.

  --enable-ansi and --disable-ansi.  This option causes stricter
     ANSI C checking to be performed when compiling with GCC. The
     default is for strict checking to be disabled. NOTE: This option
     is intended primarily as a convenience for developers.

  --enable-gimpdir=DIR.  This option changes the default directory
     the gimp uses to search for its configuration files from ~/.gimp-2.2 
     (the directory .gimp-2.2 in the users home directory) to DIR.

  --without-libtiff, --without-libjpeg, --without-libpng.  configure
     will bail out if libtiff, libjpeg or libpng can not be found. You
     better fix the underlying problem and install these libraries with
     their header files. If you absolutely want to compile GIMP without
     support for TIFF, JPEG or PNG you need to explicitely disable
     them using the options given above.
 
  --without-exif.  If libexif is available, the JPEG plug-in will use
     it to keep EXIF data in your JPEG files intact.  If this is
     causing any trouble at compile-time, you can build --without-exif.
     Get libexif from http://www.sourceforge.net/projects/libexif.

  --without-mng, --without-aa.  The MNG plug-in needs libmng and
     configure checks for its presense. If for some reason you don't
     want to build the MNG plug-in even though the library is installed,
     use --without-mng to disable it expliticely. The same switch exists
     for aalib, use --without-aa if you run into problems.

  --without-gtkhtml2.  If for some reason you don't want to build the 
     helpbrowser plug-in, you can use --without-gtkhtml2 to disable 
     it explicitly.

  --without-svg.  If for some reason you want to build GIMP without 
     SVG support, you can build --without-svg.

  --without-lcms.  If for some reason you want to build GIMP without
     using lcms for color support, you can build with --without-lcms.

  --with-gif-compression=[lzw|rle|none].  Allows to tune the compression
     algorithm used by the GIF plug-in. If you are afraid of Unisys' LZW
     patent (which should have expired in most countries by now), you
     can go for simple run-length encoding or even configure the plug-in
     to create uncompressed GIFs.

  --enable-gtk-doc.  This option controls whether the libgimp API
     references will be created using gtk-doc. The HTML pages are 
     included in a standard tarball, so you will only need this if you
     are building from CVS.

  --with-html-dir=PATH.  This option allows to specify where the
     libgimp API reference should be installed. You might want to modify
     the path so it points to the place where glib and gtk+ installled
     their API references so that the libgimp reference can link to
     them.

  --disable-print.  The print plug-in requires a recent version of
     libgimpprint. If you don't have it already installed, download
     it from http://gimp-print.sourceforge.net/. You need to pass
     --without-gimp to gimp-print's configure script to build it without
     having gimp-1.2 installed. If you want to compile GIMP without
     support for printing, use the --disable-print option.

  --enable-mp. This options control whether to build GIMP with or without
     support for multiple processors. This option is off by default. If
     you do have multiply processors and run GIMP with an OS supporting
     them you will like to enable this features to use all of your
     horsepower. Enabling it on singleprocessor systems won't harm but
     cause a bit processing overhead.

  --with-sendmail=[PATH]. This option is used to tell GIMP where to find
     the sendmail command. Normally this options don't have to be used
     because configure tries to find it in the usual places.

  --with-desktop-dir=[PATH]. This option specifies where to install
     links to the gimp desktop files. These files are used by desktop
     environments that comply to the specs published at freedesktop.org.
     The default value ${prefix}/share should be fine if your desktop
     environment is installed in the same prefix as gimp. No links are
     created if the desktop directories don't exist or you used
     --without-desktop-dir.

  --disable-default-binary. Use this option if you don't want to make
     gimp-2.2 the default gimp installation. Otherwise a link called
     gimp pointing to the gimp-2.2 executable will be installed.

  --enable-gimp-console.  In addition to the standard gimp binary,
     build a console-only binary which does not link GTK+ at all.


The `make' command builds several things:
 - A bunch of public libraries in the directories starting with 'libgimp'.
 - The plug-in programs in the 'plug-ins' directory.
 - Some modules in the 'modules' subdirectory.
 - The main GIMP program 'gimp-2.2' in `app'.

The `make install' commands installs the gimp header files associated 
with the libgimp libraries, the plug-ins, some data files and the GIMP 
executable. After running `make install' and assuming the build process 
was successful you should be able to run `gimp'.


When ./configure fails
======================

'configure' uses pkg-config, a tool that replaces the old foo-config
scripts. The most recent version is available from 
	http://www.freedesktop.org/software/pkgconfig/

'configure' tries to compile and run a short GTK+ program. There are
several reasons why this might fail:

* pkg-config could not find the file 'gtk+-2.0.pc' that gets installed 
  with GTK. (This file is used to get information about where GTK+ is
  installed.)

  Fix: Either make sure that this file is in the path where pkg-config 
  looks for it (try 'pkg-config --debug' or add the location of 
  gtk+-2.0.pc to the environment variable PKG_CONFIG_PATH before running 
  configure.

* Libraries you installed are not found when you attempt to start gimp.
  The details of how to fix this problem will depend on the system:

  On Linux and other systems using ELF libraries, add the directory to
  holding the library to /etc/ld.so.conf or to the environment variable
  LD_LIBRARY_PATH, and run 'ldconfig'.

  On other systems, it may be necessary to encode this path
  into the executable, by setting the LDFLAGS environment variable
  before running configure. For example:

    LDFLAGS="-R/home/joe/lib" ./configure
  or
    LDFLAGS="-Wl,-rpath -Wl,/home/joe/lib" ./configure

* An old version of the GTK+ libraries was found instead of 
  your newly installed version. This commonly happens if a
  binary package of GTK+ was previously installed on your system,
  and you later compiled GTK+ from source.

  Fix: Remove the old libraries and include files.  If you are afraid
  that removing the old libraries may break other packages supplied by
  your distributor, you can try installing GLib, GTK+ and other
  libraries in a different prefix after setting the environment
  variable PKG_CONFIG_LIBDIR to point to lib/pkgconfig/ in that new
  prefix so that it does not try to read the *.pc files from the
  default directory (/usr/lib/pkgconfig).  However, removing the old
  packages is often the easier solution.

A detailed log of the ./configure output is written to the file
config.log. This may help diagnose problems.


When ./configure fails on plug-ins
==================================

There are some GIMP plug-ins that need additional third-party libraries 
installed on your system. For example to compile the plug-ins that load 
and save JPEG, PNG or TIFF files you need the related libraries and header 
files installed, otherwise you'll get a message that plugin xyz will not 
be build. 

If you are sure that those libraries are correctly installed, but configure
fails to detect them, the following might help:

Set your LDFLAGS environment variable to look for the library in a certain
place, e.g. if you are working in a bash shell you would say:
      export LDFLAGS="-L<path_to_library> -L<path_to_another_one>"
before you run configure.

Set your CPPFLAGS environment variable to look for the header file in a
certain place, e.g. if you are working in a bash shell you would say:
      export CPPFLAGS="-I<path_to_header_file> -I<path_to_another_one>"
before you run configure.

* If the check for gimpprint fails even though you have version 4.2.x
  installed, please try the latest available 4.2 package (which is
  gimp-print 4.2.7 at the time of this writing).


      Generic Instructions for Building Auto-Configured Packages
      ==========================================================


To compile this package:

1.  Configure the package for your system.  In the directory that this
file is in, type `./configure'.  If you're using `csh' on an old
version of System V, you might need to type `sh configure' instead to
prevent `csh' from trying to execute `configure' itself.

The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation, and
creates the Makefile(s) (one in each subdirectory of the source
directory).  In some packages it creates a C header file containing
system-dependent definitions.  It also creates a file `config.status'
that you can run in the future to recreate the current configuration.
Running `configure' takes a minute or two.

To compile the package in a different directory from the one
containing the source code, you must use GNU make.  `cd' to the
directory where you want the object files and executables to go and
run `configure' with the option `--srcdir=DIR', where DIR is the
directory that contains the source code.  Using this option is
actually unnecessary if the source code is in the parent directory of
the one in which you are compiling; `configure' automatically checks
for the source code in `..' if it does not find it in the current
directory.

By default, `make install' will install the package's files in
/usr/local/bin, /usr/local/lib, /usr/local/man, etc.  You can specify
an installation prefix other than /usr/local by giving `configure' the
option `--prefix=PATH'.

You can specify separate installation prefixes for machine-specific
files and machine-independent files.  If you give `configure' the
option `--exec-prefix=PATH', the package will use PATH as the prefix
for installing programs and libraries.  Normally, all files are
installed using the same prefix.

`configure' ignores any other arguments that you give it.

If your system requires unusual options for compilation or linking
that `configure' doesn't know about, you can give `configure' initial
values for some variables by setting them in the environment.  In
Bourne-compatible shells, you can do that on the command line like
this:
        CC='gcc -traditional' DEFS=-D_POSIX_SOURCE ./configure

The `make' variables that you might want to override with environment
variables when running `configure' are:

(For these variables, any value given in the environment overrides the
value that `configure' would choose:)
CC              C compiler program.
                Default is `cc', or `gcc' if `gcc' is in your PATH.
INSTALL         Program to use to install files.
                Default is `install' if you have it, `cp' otherwise.
INCLUDEDIR      Directory for `configure' to search for include files.
                Default is /usr/include.

(For these variables, any value given in the environment is added to
the value that `configure' chooses:)
DEFS            Configuration options, in the form '-Dfoo -Dbar ...'
LIBS            Libraries to link with, in the form '-lfoo -lbar ...'

If you need to do unusual things to compile the package, we encourage
you to teach `configure' how to do them and mail the diffs to the
address given in the README so we can include them in the next
release.

2.  Type `make' to compile the package.

3.  Type `make install' to install programs, data files, and
documentation.

4.  You can remove the program binaries and object files from the
source directory by typing `make clean'.  To also remove the
Makefile(s), the header file containing system-dependent definitions
(if the package uses one), and `config.status' (all the files that
`configure' created), type `make distclean'.

The file `configure.in' is used as a template to create `configure' by
a program called `autoconf'.  You will only need it if you want to
regenerate `configure' using a newer version of `autoconf'.


```

---

### Post by neu2buntu on 2009-03-26
ok leave this with me!!! i take it you have some version of gimp already installed ,open terminal >applications . accessories > terminal and do code ```
gimp --version
``` and post the output too ,also what distro are you running eg ubuntu 8.10?

---

### Post by delphiexile on 2009-03-26
```

fethi@fethi-desktop:~$ gimp --version
GNU Image Manipulation Program version 2.6.3

```

Yes my distribution is Ubuntu 8.10

---

### Post by neu2buntu on 2009-03-26
right i was looking up gimpshop ,looks like you want this older version because it was modified to be more like photoshop?  the install you posted has all the info i need (you may need a few extra packages if this is your first time building from source,i cant rem of my head what all is needed,as i have built quite a few packages over time) 

by the look of things we can leave your original version of gimp intact,and perhaps install it to the /opt directory hopefully!!! this will take a bit of error shooting,but with patience we should get there  .... my next post will have the commands to run to see if the package will configure for you

---

### Post by neu2buntu on 2009-03-26
where is your file downloaded too also .is it your home directory(i think this is the default?) if so do command in terminal (use the same terminal for all these commands)
```
tar -xvjf gimpshop-2.2.11.tar.bz2
``` then ```
cd gimp-2.2.11
``` then ```
./configure
``` and post any errors

---

### Post by neu2buntu on 2009-03-26
if all the above "miracuosly" runs smoothly then in the same terminal do commands ```
make 
```then ```
sudo make install --prefix=/opt
```  .. hope this is of some help to you,i have always upgraded programs so this is a bit new to me too . dont worry if the ./configure runs and make has errors just run ```
make clean
``` in the gimpshop file ,and you can reconfigure

---

### Post by delphiexile on 2009-03-26
Unfortunately there is an error :

```


fethi@fethi-desktop:~$ cd '/media/sda5/Downloads/Linux Downloads/ADD-ONs/GIMP Shop/gimp-2.2.11/'
fethi@fethi-desktop:/media/sda5/Downloads/Linux Downloads/ADD-ONs/GIMP Shop/gimp-2.2.11$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /media/sda5/Downloads/Linux: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... f95
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether f95 accepts -g... yes
checking the maximum length of command line arguments... 32768
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
checking whether to build static libraries... no
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
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for f95 option to produce PIC... -fPIC
checking if f95 PIC flag -fPIC works... yes
checking if f95 static flag -static works... yes
checking if f95 supports -c -o file.o... yes
checking whether the f95 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether to enable maintainer-specific portions of Makefiles... no
checking for target architecture... i686-pc-linux-gnu
checking for some Win32 platform... no
checking for native Win32... no
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking whether to turn on debugging... no
checking whether to turn on profiling... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking whether time.h and sys/time.h may both be included... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking for sys/wait.h... (cached) yes
checking for unistd.h... (cached) yes
checking for pid_t... yes
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for working alloca.h... yes
checking for alloca... yes
checking for difftime... yes
checking for putenv... yes
checking for mmap... yes
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
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
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  bg ca cs da de el en_CA en_GB es eu fi fr ga gl he hu hr id it ja ko lt mk ms nb nl no pa pl pt pt_BR ro ru sk sr sr@Latn sv tr uk vi yi zh_CN zh_TW
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.4.5... yes (version 2.18.2)
checking pkg-config is at least version 0.9.0... yes
checking for GMODULE... yes
checking if GLib is version 2.7.0 or newer... yes
checking for bind_textdomain_codeset... (cached) yes
checking for X... libraries , headers in standard search path
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GTK+ - version >= 2.4.4... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
[COLOR="Red"]**configure: error: Test for GTK+ failed. See the file 'INSTALL' for help.**[/COLOR]



```

---

### Post by neu2buntu on 2009-03-26
right we will need to goto the synaptic package manager by >system > administration >synaptic package manager... goto the "search" option (magnifying glass icon) and type "freetype" and from this list install = fontconfig, libfreetype6 ,libfreetype6-dev,all libpango programs, ----just mark these for installation,then do another search for "gtk+"  and make sure it is at least 
GTK+ version 2.4.4 or better (mark for installation,if not already installed) next search "glib" and install latest version too , also if any packages have "-dev" files install them too .....now tick apply to install them all.....try and run configure again by 
```
cd gimp-2.2.11
``` and ```
./configure
``` from a new terminal

---

### Post by delphiexile on 2009-03-26
I'll try that right now ..

---

### Post by delphiexile on 2009-03-26
The same error occures

---

### Post by delphiexile on 2009-03-27
Is there anyone here

---

### Post by delphiexile on 2009-03-27
OK , i found a deb package of this program , thank you all

---

### Post by neu2buntu on 2009-03-27
ok you still not got any further?...lol...

---

### Post by neu2buntu on 2009-03-27
deb packages are way much easier,but @least you learned how to "cd"to a directory........i actually downloaded your program and will try to install it(although im scared of breaking some other stuff...lol...)...wonder what was wrong that ./configure didnt work.....i will find this out as i will install your prog (leave it till tommorrow as im consuming alcohol now,...lol..,...)...well anyway goodluck!!!

---

### Post by delphiexile on 2009-10-16
> **neu2buntu said:**
> deb packages are way much easier,but @least you learned how to "cd"to a directory........i actually downloaded your program and will try to install it(although im scared of breaking some other stuff...lol...)...wonder what was wrong that ./configure didnt work.....i will find this out as i will install your prog (leave it till tommorrow as im consuming alcohol now,...lol..,...)...well anyway goodluck!!!


I know even how to install .tar.gz packages , but this i got troubles with , thanks anyway to all who posted in this thread.

---

### Post by phillw on 2009-10-16
> **delphiexile said:**
> OK , i found a deb package of this program , thank you all


do pop back on and say what you think of GIMPShop Vs GIMP and how similar / dissiamilar it is to photoshop .

As for deb pkg - I'd say most apps are available in at least deb packages - for those that aren't I find alien does a good job :)


Thanks,

Phill.

---

