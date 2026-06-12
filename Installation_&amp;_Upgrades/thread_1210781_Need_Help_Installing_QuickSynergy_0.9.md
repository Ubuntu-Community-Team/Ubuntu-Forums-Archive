---
title: "Need Help Installing QuickSynergy 0.9"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by Evildemon989 on 2009-07-11
So, I've already installed QuickSynergy onto my Macbook, and now I'm in the process of installing 0.9 onto my ubuntu box. I have the folder needed to install it(it's called "quicksynergy-0.9.0"). In the install instructions, it says this:

>  The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, and a
file `config.log' containing compiler output (useful mainly for
debugging `configure').

   It can also use an optional file (typically called `config.cache'
and enabled with `--cache-file=config.cache' or simply `-C') that saves
the results of its tests to speed up reconfiguring.  (Caching is
disabled by default to prevent problems with accidental use of stale
cache files.)

   If you need to do unusual things to compile the package, please try
to figure out how `configure' could check whether to do them, and mail
diffs or instructions to the address given in the `README' so they can
be considered for the next release.  If you are using the cache, and at
some point `config.cache' contains results you don't want to keep, you
may remove or edit it.

   The file `configure.ac' (or `configure.in') is used to create
`configure' by a program called `autoconf'.  You only need
`configure.ac' if you want to change it or regenerate `configure' using
a newer version of `autoconf'.

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

So, I cd'd to the directory, and ran "./configure". This is where I ran into problems. I then tried to "make" it. It didn't work. What should I do now?

---

### Post by Partyboi2 on 2009-07-11
Hi, make sure you have the build-essential package installed first
```
sudo apt-get install build-essential
```then cd into the source directory (like you have done) and run
./configure and install any packages that it requires before running 'make'.

Edit: There is a version of QuickSynergy in the Ubuntu repos, you can install it instead of having to compile if you don't mind a slightly older version.

---

### Post by jerrrys on 2009-07-11
if you want a GUI, why not just get it from the repositories (Synaptic)

[https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)

---

### Post by Evildemon989 on 2009-07-12
> **Partyboi2 said:**
> Hi, make sure you have the build-essential package installed first
```
sudo apt-get install build-essential
```then cd into the source directory (like you have done) and run
./configure and install any packages that it requires before running 'make'.

Edit: There is a version of QuickSynergy in the Ubuntu repos, you can install it instead of having to compile if you don't mind a slightly older version.

Ok, so I installed build-essential, and I ran ./configure again. This is what it put out:

> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for gethostname... yes
checking for mkdir... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.10.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

So, I'm guessing that now I have to install "gtk+-2.0"?

And also, I know there is a synergy build in the repos but I want the newest version.

---

### Post by Evildemon989 on 2009-07-12
Bump

---

### Post by Partyboi2 on 2009-07-13
You will need to install the libgtk2.0-dev package
```
sudo apt-get install libgtk2.0-dev
```

---

### Post by Evildemon989 on 2009-07-13
Well, I got father after I installed libgtk2.0-dev.

I run ./configure now, and it works. I run make, and this is what I get(I'm not sure if there is anything wrong here:

```
hadrian@hadrian-desktop:~/Desktop/quicksynergy-0.9.0$ make
make  all-recursive
make[1]: Entering directory `/home/hadrian/Desktop/quicksynergy-0.9.0'
Making all in po
make[2]: Entering directory `/home/hadrian/Desktop/quicksynergy-0.9.0/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/hadrian/Desktop/quicksynergy-0.9.0/po'
Making all in src/logo
make[2]: Entering directory `/home/hadrian/Desktop/quicksynergy-0.9.0/src/logo'
gdk-pixbuf-csource --raw --extern --build-list qslogo ./qslogo.png > qslogo.h
make[2]: Leaving directory `/home/hadrian/Desktop/quicksynergy-0.9.0/src/logo'
Making all in src
make[2]: Entering directory `/home/hadrian/Desktop/quicksynergy-0.9.0/src'
gcc -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT synergy_config.o -MD -MP -MF .deps/synergy_config.Tpo -c -o synergy_config.o synergy_config.c
synergy_config.c: In function ‘load_config’:
synergy_config.c:36: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
synergy_config.c: In function ‘save_config’:
synergy_config.c:92: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
synergy_config.c: In function ‘save_synergy_config’:
synergy_config.c:132: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
mv -f .deps/synergy_config.Tpo .deps/synergy_config.Po
gcc -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT callbacks.o -MD -MP -MF .deps/callbacks.Tpo -c -o callbacks.o callbacks.c
callbacks.c:50: warning: initialization from incompatible pointer type
callbacks.c:51: warning: initialization from incompatible pointer type
callbacks.c: In function ‘browse_button_clicked’:
callbacks.c:114: warning: passing argument 1 of ‘gtk_entry_set_text’ from incompatible pointer type
callbacks.c: In function ‘start_button_clicked’:
callbacks.c:171: warning: ignoring return value of ‘chdir’, declared with attribute warn_unused_result
mv -f .deps/callbacks.Tpo .deps/callbacks.Po
gcc -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT ui.o -MD -MP -MF .deps/ui.Tpo -c -o ui.o ui.c
mv -f .deps/ui.Tpo .deps/ui.Po
gcc -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -g -O2 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
mv -f .deps/main.Tpo .deps/main.Po
gcc  -g -O2   -o quicksynergy synergy_config.o callbacks.o ui.o main.o -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0   
make[2]: Leaving directory `/home/hadrian/Desktop/quicksynergy-0.9.0/src'
make[2]: Entering directory `/home/hadrian/Desktop/quicksynergy-0.9.0'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/hadrian/Desktop/quicksynergy-0.9.0'
make[1]: Leaving directory `/home/hadrian/Desktop/quicksynergy-0.9.0'

```

And just incase it did work right, I ran "make install" and this is definitely wrong:

```
hadrian@hadrian-desktop:~/Desktop/quicksynergy-0.9.0$ make installMaking install in po
make[1]: Entering directory `/home/hadrian/Desktop/quicksynergy-0.9.0/po'
/bin/mkdir -p /usr/local/share
/bin/mkdir: cannot create directory `/usr/local/share/locale': Permission denied
/usr/bin/install: cannot create regular file `/usr/local/share/locale/pt_BR/LC_MESSAGES/quicksynergy.mo': No such file or directory
installing pt_BR.gmo as /usr/local/share/locale/pt_BR/LC_MESSAGES/quicksynergy.mo
if test "quicksynergy" = "gettext-tools"; then \
	  /bin/mkdir -p /usr/local/share/gettext/po; \
	  for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed en@quot.header en@boldquot.header insert-header.sin Rules-quot   Makevars.template; do \
	    /usr/bin/install -c -m 644 ./$file \
			    /usr/local/share/gettext/po/$file; \
	  done; \
	  for file in Makevars; do \
	    rm -f /usr/local/share/gettext/po/$file; \
	  done; \
	else \
	  : ; \
	fi
make[1]: Leaving directory `/home/hadrian/Desktop/quicksynergy-0.9.0/po'
Making install in src/logo
make[1]: Entering directory `/home/hadrian/Desktop/quicksynergy-0.9.0/src/logo'
make[2]: Entering directory `/home/hadrian/Desktop/quicksynergy-0.9.0/src/logo'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/hadrian/Desktop/quicksynergy-0.9.0/src/logo'
make[1]: Leaving directory `/home/hadrian/Desktop/quicksynergy-0.9.0/src/logo'
Making install in src
make[1]: Entering directory `/home/hadrian/Desktop/quicksynergy-0.9.0/src'
make[2]: Entering directory `/home/hadrian/Desktop/quicksynergy-0.9.0/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'quicksynergy' '/usr/local/bin/quicksynergy'
/usr/bin/install: cannot create regular file `/usr/local/bin/quicksynergy': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/hadrian/Desktop/quicksynergy-0.9.0/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/hadrian/Desktop/quicksynergy-0.9.0/src'
make: *** [install-recursive] Error 1
```

So I'm not sure what to do next?

---

### Post by Partyboi2 on 2009-07-14
Instead of 'make install' use
```
sudo make install
```

---

### Post by TRG1 on 2010-03-06
I have been using Synergy for some time between two Windows computers... works great. Today I replaced XP on one of the machines with ubuntu and I'm trying to get Synergy back up.  I've read the relevant threads and instructions, but I'm not getting anywhere. I am going to have to have someone cookbook this for me. So far I have downloaded  QuickSynergy which is supposed to install the application.  It seems to run, but I see no evidence of it on my machine.  What am I supposed to do next?

Thanks in advance.

tom

edit: When I run the installer everything appears to go as it should and when I look at the list of installed applications in ...applications/addremove... QuickSynergy appears there, but it does not appear in the app menu?

I was just poking around the system and wound up at the update manager where it said an update was available for QuickSynergy.  As soon as I downloaded the update everything started working.  Back in business:-)

---

