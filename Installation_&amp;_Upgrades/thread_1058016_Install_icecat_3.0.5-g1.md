---
title: "Install icecat 3.0.5-g1"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by obl on 2009-02-02
Hey guys. Downloaded the tar.bz2 but have no idea how to install it. Any ideas?

---

### Post by Partyboi2 on 2009-02-03
Open a terminal (Applications>Accessories>Terminal) and install build-essential package
```
sudo apt-get install build-essential
``` Then use the cd command to change to the location where you have downloaded the icecat-3.0.5-g1.tar.bz2 file. So for example if its on your Desktop
```
cd ~/Desktop
```Then extract it
```
tar xvjf icecat-3.0.5-g1.tar.bz2 
``` Once extracted enter the newly created directory
```
cd icecat-3.0.5-g1
``` Then type
```
./configure
``` If that finishes with no errors on does not complain about missing packages you can then build it by typing
```
make
``` If make finishes without error then you can proceed to install
```
sudo make install
```Edit: If you don't mind a older version of icecat (2.0)  you can add 
```
 deb http://http.us.debian.org/debian unstable main
``` to your sources.list in Software Sources (System>Admin>Software Sources>3rd Party) then install with
```
sudo apt-get install iceweasel
```If you install 2.0 I would suggest removing or disabling the deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) repo afterwards.


Edit: The debian repo now has version 3.06

---

### Post by rdiggs on 2009-02-03
What do you do if ./configure shows missing packages? Where do you get them and how can I continue?

---

### Post by Partyboi2 on 2009-02-03
You can search through Synaptic (System>Admin>Synaptic Package Manager) for the packages required and install them. What ever package is listed as needed to compile the program you will need to install the development package (dev)
If you are not sure what package you need to install then post a list of the missing packages.

---

### Post by jProteus on 2009-02-09
Hey there. I'm having trouble with this as well. I've been trying to figure out how to acquire the dependencies, but I'm not having any luck. Here's what I'm missing:

Package gtk+-2.0 was not found in the pkg-config search path. 
Package gtk+-unix-print-2.0 was not found in the pkg-config search path. 
Package gdk-x11-2.0 was not found in the pkg-config search path. 
Package glib-2.0 was not found in the pkg-config search path. 
Package gobject-2.0 was not found in the pkg-config search path. 

Library requirements (gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 gdk-x11-2.0 glib-2.0 gobject-2.0)

---

### Post by agonx on 2009-02-09
```
sudo apt-get install libgtk2.0-dev
```
this may work
If you still get errors
you may need 
```

sudo apt-get install libdbus-glib-1-dev
sudo apt-get install libidl-dev

```

---

### Post by nico_forgot on 2009-03-03
i've gotten everything done up to configuring. that all went well. i entered the make command and it ended with a lot of error notices:

ErrorUtils.cpp:273: error: expected constructor, destructor, or type conversion before ‘*’ token
ErrorUtils.cpp: In function ‘nsresult PyXPCOM_SetCOMErrorFromPyException()’:
ErrorUtils.cpp:284: error: ‘PyErr_Occurred’ was not declared in this scope
ErrorUtils.cpp:288: error: ‘PyExc_MemoryError’ was not declared in this scope
ErrorUtils.cpp:288: error: ‘PyErr_ExceptionMatches’ was not declared in this scope
ErrorUtils.cpp:296: error: ‘PyErr_Clear’ was not declared in this scope
ErrorUtils.cpp: At global scope:
ErrorUtils.cpp:308: error: redefinition of ‘char* PyTraceback_AsString’
ErrorUtils.cpp:53: error: ‘char* PyTraceback_AsString’ previously defined here
ErrorUtils.cpp:308: error: ‘PyObject’ was not declared in this scope
ErrorUtils.cpp:308: error: ‘exc_tb’ was not declared in this scope
make[5]: *** [ErrorUtils.o] Error 1

how do i fix these errors before proceeding to make install (or checkinstall)? cheers - nico

---

### Post by aztecaribe on 2009-03-05
Hi.
im trying to compile icecat but i can create te make file, when i run ./configure this is the output i got.

[I]Adding configure options from ./.mozconfig:
  --disable-ldap
  --disable-calendar
  --disable-mailnews
  --disable-chatzilla
  --enable-extensions=default cookie permissions python/xpcom spellcheck
  --enable-crypto
  --disable-composer
  --enable-single-profile
  --disable-profilesharing
  --disable-debug
  --enable-toolkit-cairo-gtk2
  --enable-default-toolkit=cairo-gtk2
  --enable-xft
  --disable-freetype2
  --disable-tests
  --disable-mochitest
  --disable-debug
  --disable-accessibility
  --enable-strip
  --disable-toolkit-qt
  --prefix=/usr/local
  --disable-pango
  --disable-xprint
  --with-user-appdir=.gnuzilla
  --disable-xinerama
  --with-system-zlib
  --with-system-jpeg
  --enable-svg
  --enable-svg-renderer=cairo
  --enable-application=browser
  --disable-system-cairo
  --disable-negotiateauth
  --disable-installer
  --disable-updater
  --disable-elf-dynstr-gc
  --with-distribution-id=org.gnu.gnuzilla
  --disable-crashreporter
  --with-branding=browser/branding/unofficial
  --disable-official-branding
  --enable-optimize=-pipe -O2
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gawk... no
checking for mawk... mawk
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking for ranlib... ranlib
checking for as... /usr/bin/as
checking for ar... ar
checking for ld... ld
checking for strip... strip
checking for windres... no
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking how to run the C++ preprocessor... c++ -E
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for perl5... no
checking for perl... /usr/bin/perl
checking for minimum required perl version >= 5.006... 5.010000
checking for full perl installation... yes
checking for python... /usr/bin/python
PYTHON=/usr/bin/python
checking for nsinstall... no
checking for doxygen... :
checking for whoami... /usr/bin/whoami
checking for autoconf... :
checking for unzip... /usr/bin/unzip
checking for zip... /usr/bin/zip
checking for makedepend... no
checking for xargs... /usr/bin/xargs
checking for gmake... no
checking for make... /usr/bin/make
checking for X... no
checking whether ld has archive extraction flags... yes
checking that static assertion macros used in autoconf tests work... yes
checking for 64-bit OS... no
checking for ANSI C header files... yes
checking for working const... yes
checking for mode_t... yes
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for st_blksize in struct stat... yes
checking for siginfo_t... yes
checking for int16_t... yes
checking for int32_t... yes
checking for int64_t... yes
checking for int64... no
checking for uint... yes
checking for uint_t... no
checking for uint16_t... no
checking for uname.domainname... yes
checking for uname.__domainname... no
checking for usable wchar_t (2 bytes, unsigned)... no
checking for compiler -fshort-wchar option... yes
checking for visibility(hidden) attribute... yes
checking for visibility(default) attribute... yes
checking for visibility pragma support... yes
checking For gcc visibility bug with class-level attributes (GCC bug 26905)... no
checking For x86_64 gcc visibility bug with builtins (GCC bug 20297)... no
checking for dirent.h that defines DIR... yes
checking for opendir in -ldir... no
checking for sys/byteorder.h... no
checking for compat.h... no
checking for getopt.h... yes
checking for sys/bitypes.h... yes
checking for memory.h... yes
checking for unistd.h... yes
checking for gnu/libc-version.h... yes
checking for nl_types.h... yes
checking for malloc.h... yes
checking for X11/XKBlib.h... yes
checking for sys/statvfs.h... yes
checking for sys/statfs.h... yes
checking for sys/vfs.h... yes
checking for sys/mount.h... yes
checking for mmintrin.h... no
checking for new... yes
checking for sys/cdefs.h... yes
checking for gethostbyname_r in -lc_r... no
checking for atan in -lm... yes
checking for dlopen in -ldl... yes
checking for dlfcn.h... yes
checking for dladdr... yes
checking for socket in -lsocket... no
checking for pthread_create in -lpthreads... no
checking for pthread_create in -lpthread... yes
checking whether gcc accepts -pthread... yes
checking whether mmap() sees write()s... yes
checking whether gcc needs -traditional... no
checking for 8-bit clean memcmp... yes
checking for random... yes
checking for strerror... yes
checking for lchown... yes
checking for fchmod... yes
checking for snprintf... yes
checking for statvfs... yes
checking for memmove... yes
checking for rint... yes
checking for stat64... yes
checking for lstat64... yes
checking for truncate64... yes
checking for statvfs64... yes
checking for flockfile... yes
checking for getpagesize... yes
checking for localtime_r... yes
checking for strtok_r... yes
checking for wcrtomb... yes
checking for mbrtowc... yes
checking for res_ninit()... yes
checking for gnu_get_libc_version()... yes
checking for iconv in -lc... yes
checking for iconv()... yes
checking for iconv() with const input... no
checking for nl_langinfo and CODESET... yes
checking for an implementation of va_copy()... yes
checking for an implementation of __va_copy()... yes
checking whether va_lists can be copied by value... yes
checking for C++ exceptions flag... -fno-exceptions
checking for gcc 3.0 ABI... yes
checking for C++ "explicit" keyword... yes
checking for C++ "typename" keyword... yes
checking for modern C++ template specialization syntax support... yes
checking whether partial template specialization works... yes
checking whether operators must be re-defined for templates derived from templates... no
checking whether we need to cast a derived template to pass as its base class... no
checking whether the compiler can resolve const ambiguities for templates... yes
checking whether the C++ "using" keyword can change access... yes
checking whether the C++ "using" keyword resolves ambiguity... yes
checking for "std::" namespace... yes
checking whether standard template operator!=() is ambiguous... unambiguous
checking for C++ reinterpret_cast... yes
checking for C++ dynamic_cast to void*... yes
checking whether C++ requires implementation of unused virtual methods... yes
checking for trouble comparing to zero near std::operator!=()... no
checking for LC_MESSAGES... yes
checking for jpeg_destroy_compress in -ljpeg... no
checking for gzread in -lz... yes
checking if app-specific confvars.sh exists... ./browser/confvars.sh
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 gdk-x11-2.0 glib-2.0 gobject-2.0... yes
checking MOZ_GTK2_CFLAGS... -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gtk-unix-print-2.0  
checking MOZ_GTK2_LIBS... -lgtk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lfreetype -lz -lfontconfig -lgdk-x11-2.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lpango-1.0 -lcairo -lgmodule-2.0 -lgobject-2.0 -lglib-2.0  
checking for xft... yes
checking MOZ_XFT_CFLAGS... -I/usr/include/freetype2  
checking MOZ_XFT_LIBS... -lXft  
checking for pango >= 1.10.0... yes
checking _PANGOCHK_CFLAGS... -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking _PANGOCHK_LIBS... -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
checking for pango >= 1.10.0 pangocairo >= 1.10.0 pangoft2 >= 1.10.0... yes
checking MOZ_PANGO_CFLAGS... -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
checking MOZ_PANGO_LIBS... -lpangocairo-1.0 -lcairo -lpangoft2-1.0 -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
checking for gnome-vfs-2.0 >= 2.0 gnome-vfs-module-2.0 >= 2.0... checking for gconf-2.0 >= 1.2.1... checking for libgnome-2.0 >= 2.0... checking for libgnomeui-2.0 >= 2.2.0... checking for dbus-glib-1 >= 0.60... yes
checking MOZ_DBUS_GLIB_CFLAGS... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking MOZ_DBUS_GLIB_LIBS... -L//lib -ldbus-glib-1 -ldbus-1 -lgobject-2.0 -lglib-2.0  
configure: warning: Cannot build gnomevfs without required libraries. Removing gnomevfs from MOZ_EXTENSIONS.
configure: warning: cookie and permissions are no longer extensions, use --disable-permissions to disable.
configure: warning: spellcheck is no longer an extension.
checking for tar archiver... checking for gnutar... no
checking for gtar... no
checking for tar... tar
tar
checking for wget... checking for wget... wget
wget
checking for valid optimization flags... yes
checking size of int *... 4
checking for valgrind/valgrind.h... no
checking for __builtin_vec_new... no
checking for __builtin_vec_delete... no
checking for __builtin_new... no
checking for __builtin_delete... no
checking for __pure_virtual... no
checking for __cxa_demangle... yes
checking for unwind.h... yes
checking for _Unwind_Backtrace... yes
checking for gcc -pipe support... cat: dummy-hello.s: No such file or directory
yes
checking whether compiler supports -Wno-long-long... yes
checking whether C compiler supports -fprofile-generate... yes
checking whether C++ compiler has -pedantic long long bug... no
checking for correct temporary object destruction order... yes
checking for correct overload resolution with const and templates... no
checking for libIDL-2.0 >= 0.8.0 glib-2.0 gobject-2.0... yes
checking LIBIDL_CFLAGS... -I/usr/include/libIDL-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking LIBIDL_LIBS... -lIDL-2 -lgobject-2.0 -lglib-2.0  
checking for glib-2.0 >= 1.3.7 gobject-2.0... yes
checking GLIB_CFLAGS... -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking GLIB_LIBS... -lgobject-2.0 -lglib-2.0  
checking for stdint.h... yes
checking for inttypes.h... yes
checking for sys/int_types.h... no
Building Python extensions using python-2.5 from /usr
configure: error: Could not compile basic X program.[/I]

what is wrong? how can i fix it and create the make?
i already install libgtk2.0-dev, libdbus-glib-1-dev and libidl-dev.
TNX for any help.

---

### Post by Partyboi2 on 2009-03-05
Have you tried adding the 3rd party repo that I posted and tried installing 3.0.6 instead of 3.0.5?

---

### Post by nico_forgot on 2009-03-05
i thought that the repo you posted was for iceweasel (i know it's icecat's predecessor) 2.0. i tried it with the hopes that my update manager would bring up to speed but when i i attempted an install in the terminal i was told the package is obsolete.
i'm still trying to deal with the error messages that i got in the make process. missing packages i can fix. error messages like the ones i got are beyond me. thanks. cheers - nico

---

### Post by aztecaribe on 2009-03-06
as nico said partyboi2, the support on synaptic is for iceweasel not for ice cat.

in my case was a type mistake im installing  icecat 3.0.6.

what this error mean?

*configure: error: Could not compile basic X program.*

how do i fix this? wich library is missing? there are no .dev of icecat. only the .tar.bz2 here the [link]("ftp://ftp.gnu.org/gnu/gnuzilla/")

again tnx 4 any help

---

### Post by Partyboi2 on 2009-03-06
> **aztecaribe said:**
> as nico said partyboi2, the support on synaptic is for iceweasel not for ice cat.

in my case was a type mistake im installing  icecat 3.0.6.

what this error mean?

*configure: error: Could not compile basic X program.*

how do i fix this? wich library is missing? there are no .dev of icecat. only the .tar.bz2 here the [link]("ftp://ftp.gnu.org/gnu/gnuzilla/")

again tnx 4 any help
My mistake, I thought icecat was just a name change for iceweasel. When I ran into that  error, I looked  at the config log and found that I needed to install libxt-dev

---

### Post by aztecaribe on 2009-03-06
ok, finally the configure end without error, just with a warning

*configure: warning: Recreating autoconf.mk with updated nspr-config output*

then i run the make, it take a lot of time (aprox 20 min) and i got this errors

[I]make[5]: se sale del directorio `/home/ame/Escritorio/icecat-3.0.6-g1/extensions/python/xpcom/src'
make[4]: se sale del directorio `/home/ame/Escritorio/icecat-3.0.6-g1/extensions/python/xpcom'
make[3]: se sale del directorio `/home/ame/Escritorio/icecat-3.0.6-g1/extensions'
make[2]: se sale del directorio `/home/ame/Escritorio/icecat-3.0.6-g1'
make[1]: se sale del directorio `/home/ame/Escritorio/icecat-3.0.6-g1'[/I]

then i run make again and i got this errors
[I]ErrorUtils.cpp: At global scope:
ErrorUtils.cpp:53: error: ‘PyObject’ no se declaró en este ámbito
ErrorUtils.cpp:53: error: ‘exc_tb’ no se declaró en este ámbito
ErrorUtils.cpp:85: aviso: ‘pyxpcom_initialized’ inicializado y declarado como ‘extern’
ErrorUtils.cpp: In function ‘void DoLogMessage(const char*, const char*)’:
ErrorUtils.cpp:103: error: ‘PyObject’ no se declaró en este ámbito
ErrorUtils.cpp:103: error: ‘exc_typ’ no se declaró en este ámbito
ErrorUtils.cpp:103: error: ‘exc_val’ no se declaró en este ámbito
ErrorUtils.cpp:103: error: ‘exc_tb’ no se declaró en este ámbito
ErrorUtils.cpp:104: error: ‘PyErr_Fetch’ no se declaró en este ámbito
ErrorUtils.cpp:114: error: ‘mod’ no se declaró en este ámbito
ErrorUtils.cpp:114: error: ‘PyImport_ImportModule’ no se declaró en este ámbito
ErrorUtils.cpp:115: error: ‘logger’ no se declaró en este ámbito
ErrorUtils.cpp:116: error: ‘PyObject_CallMethod’ no se declaró en este ámbito
ErrorUtils.cpp:118: error: ‘handlers’ no se declaró en este ámbito
ErrorUtils.cpp:118: error: ‘PyObject_GetAttrString’ no se declaró en este ámbito
ErrorUtils.cpp:120: error: ‘PySequence_Check’ no se declaró en este ámbito
ErrorUtils.cpp:121: error: ‘PySequence_Length’ no se declaró en este ámbito
ErrorUtils.cpp:122: error: ‘Py_XDECREF’ no se declaró en este ámbito
ErrorUtils.cpp:125: error: ‘PyErr_Clear’ no se declaró en este ámbito
ErrorUtils.cpp:139: error: ‘obMessage’ no se declaró en este ámbito
ErrorUtils.cpp:139: error: ‘PyString_FromString’ no se declaró en este ámbito
ErrorUtils.cpp:141: error: ‘repr’ no se declaró en este ámbito
ErrorUtils.cpp:141: error: ‘PyObject_Repr’ no se declaró en este ámbito
ErrorUtils.cpp:143: error: ‘PyString_AsString’ no se declaró en este ámbito
ErrorUtils.cpp:144: error: ‘Py_DECREF’ no se declaró en este ámbito
ErrorUtils.cpp:146: error: ‘Py_DECREF’ no se declaró en este ámbito
ErrorUtils.cpp:149: error: ‘PyRun_SimpleString’ no se declaró en este ámbito
ErrorUtils.cpp:152: error: ‘PyErr_Restore’ no se declaró en este ámbito
ErrorUtils.cpp: In function ‘void LogMessage(const char*, const char*)’:
ErrorUtils.cpp:159: error: ‘PyObject’ no se declaró en este ámbito
ErrorUtils.cpp:159: error: ‘exc_typ’ no se declaró en este ámbito
ErrorUtils.cpp:159: error: ‘exc_val’ no se declaró en este ámbito
ErrorUtils.cpp:159: error: ‘exc_tb’ no se declaró en este ámbito
ErrorUtils.cpp:160: error: ‘PyErr_Fetch’ no se declaró en este ámbito
ErrorUtils.cpp:162: error: ‘PyErr_Restore’ no se declaró en este ámbito
ErrorUtils.cpp: In function ‘PRBool PyXPCOM_FormatCurrentException(nsCString_external&)’:
ErrorUtils.cpp:186: error: ‘PyObject’ no se declaró en este ámbito
ErrorUtils.cpp:186: error: ‘exc_typ’ no se declaró en este ámbito
ErrorUtils.cpp:186: error: ‘exc_val’ no se declaró en este ámbito
ErrorUtils.cpp:186: error: ‘exc_tb’ no se declaró en este ámbito
ErrorUtils.cpp:187: error: ‘PyErr_Fetch’ no se declaró en este ámbito
ErrorUtils.cpp:188: error: ‘PyErr_NormalizeException’ no se declaró en este ámbito
ErrorUtils.cpp:193: error: ‘PyErr_Restore’ no se declaró en este ámbito
ErrorUtils.cpp: At global scope:
ErrorUtils.cpp:198: error: ‘PyObject’ no se ha declarado
ErrorUtils.cpp:198: error: ‘PyObject’ no se ha declarado
ErrorUtils.cpp:199: error: ‘PyObject’ no se ha declarado
ErrorUtils.cpp: In function ‘PRBool PyXPCOM_FormatGivenException(nsCString_external&, int*, int*, int*)’:
ErrorUtils.cpp:206: error: no se puede usar ‘PyTraceback_AsString’ como una función
ErrorUtils.cpp:212: error: ‘PyMem_Free’ no se declaró en este ámbito
ErrorUtils.cpp:215: error: ‘PyObject’ no se declaró en este ámbito
ErrorUtils.cpp:215: error: ‘temp’ no se declaró en este ámbito
ErrorUtils.cpp:215: error: ‘PyObject_Str’ no se declaró en este ámbito
ErrorUtils.cpp:217: error: ‘PyString_AsString’ no se declaró en este ámbito
ErrorUtils.cpp:218: error: ‘Py_DECREF’ no se declaró en este ámbito
ErrorUtils.cpp:225: error: ‘PyString_AsString’ no se declaró en este ámbito
ErrorUtils.cpp:226: error: ‘Py_DECREF’ no se declaró en este ámbito
ErrorUtils.cpp: At global scope:
ErrorUtils.cpp:273: error: expected constructor, destructor, or type conversion before ‘*’ token
ErrorUtils.cpp: In function ‘nsresult PyXPCOM_SetCOMErrorFromPyException()’:
ErrorUtils.cpp:284: error: ‘PyErr_Occurred’ no se declaró en este ámbito
ErrorUtils.cpp:288: error: ‘PyExc_MemoryError’ no se declaró en este ámbito
ErrorUtils.cpp:288: error: ‘PyErr_ExceptionMatches’ no se declaró en este ámbito
ErrorUtils.cpp:296: error: ‘PyErr_Clear’ no se declaró en este ámbito
ErrorUtils.cpp: At global scope:
ErrorUtils.cpp:308: error: redefinition of ‘char* PyTraceback_AsString’
ErrorUtils.cpp:53: error: se definió ‘char* PyTraceback_AsString’ previamente aquí
ErrorUtils.cpp:308: error: ‘PyObject’ no se declaró en este ámbito
ErrorUtils.cpp:308: error: ‘exc_tb’ no se declaró en este ámbito
make[5]: *** [ErrorUtils.o] Error 1
make[4]: *** [libs] Error 2
make[3]: *** [libs] Error 2
make[2]: *** [libs_tier_app] Error 2
make[1]: *** [tier_app] Error 2
make: *** [default] Error 2[/I]

any idea about what is wrong? 
its important to fix the configure warning?how?
how do i can run make whitout errors?
for extended error info watch any of this (its the same file but in diferent hosts)

[error files]("http://www.gigasize.com/get.php?d=fjqzyxzjdfb")
[error files]("http://uploading.com/files/7E7CY98M/IcecatErrors.zip.html")
[error files]("http://www.turboupload.com/files/get/l1orRGYi0o/icecaterrors.zip")
[error files]("http://www.fileqube.com/hl/boXRYPbko1374625/IcecatErrors.zip")
[error files]("http://www.filedropper.com/icecaterrors")
[error files]("http://www.badongo.com/file/13728642")
[error files]("http://www.easy-share.com/1903920648/IcecatErrors.zip")

---

### Post by sports fan Matt on 2009-03-06
Whats the difference between Icecat and Firefox?

---

### Post by aztecaribe on 2009-03-09
> **sox fan Matt said:**
> Whats the difference between Icecat and Firefox?

IceCat is the GNU version of the Firefox browser. Its main advantage is an ethical one: it is entirely free software. While the source code from the Mozilla project is free software, the binaries that they release include additional non-free software. Also, they distribute and recommend non-free software as plug-ins.

In addition, GNU IceCat includes some privacy protection features, included in a separate addon:

   1. Some sites refer to zero-size images on other hosts to keep track of cookies. When IceCat detects this mechanism it blocks cookies from the site hosting the zero-length image file. (It is possible to re-enable such a site by removing it from the blocked hosts list.)
   2. Other sites rewrite the host name in links redirecting the user to another site, mainly to "spy" on clicks. When this behavior is detected, IceCat shows a message alerting the user.

Please, anyone can helpme with my Icecat errors?

---

### Post by aztecaribe on 2009-03-11
F111111111!!!!!!!  F111111111!!!!!!!!

---

