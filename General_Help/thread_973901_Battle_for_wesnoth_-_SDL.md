---
title: "Battle for wesnoth - SDL"
date: 2008-11-07
forum: General Help
---

### Post by malcolmx82 on 2008-11-07
Hi everybody..
i've read the other post but didnt' manage to solve the problem..
i downloaded the source from the web site and extracted it into /usr/src

then i ran ./configure and got this

```
marco@marco-laptop:/usr/src/wesnoth-1.4.5$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
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
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for ranlib... ranlib
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for XOpenDisplay in -lX11... yes
checking for pngmeta... no
checking for sdl-config... no
checking for sdl11-config... no
configure: error: *** SDL not found! Get SDL from www.libsdl.org.
If you already installed it, check it's in the path. If problem remains,
please send a mail to the address that appears in ./configure --version
indicating your platform, the version of configure script and the problem.
```

via synaptic I installed libsdl1.2-dev and again i run ./configure
and again i got this

```
marco@marco-laptop:/usr/src/wesnoth-1.4.5$ ./configure 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
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
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for ranlib... ranlib
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for XOpenDisplay in -lX11... yes
checking for pngmeta... no
checking for sdl-config... /usr/bin/sdl-config
checking for fribidi-config... no
configure: WARNING: *** FRIBIDI not found.
checking for python... /usr/bin/python
checking Python version and location... /usr/bin/python, 2.5, /usr
checking whether Python is at least 2.4... yes
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
checking Python.h usability... no
checking Python.h presence... no
checking for Python.h... no
configure: WARNING: *** Python include files not found! You should install Python development package. Python support disabled
checking for libpng-config... /usr/bin/libpng-config
checking for SDL - version >= 1.2.7... yes
checking for po4a... no
checking for asciidoc... no
checking for dos2unix... no
checking for xsltproc... /usr/bin/xsltproc
checking for libtool... no
checking for IMG_Load in -lSDL_image... no
configure: error: *** SDL_image lib not found! Get SDL_image from
http://www.libsdl.org/projects/SDL_image/index.html
```

how can i solve the problem?
thanks

---

### Post by Tim Sharitt on 2008-11-07
Try 
```
sudo apt-get build-dep wesnoth
```
This should install all of the packages needed to build.

---

### Post by malcolmx82 on 2008-11-08
> **Tim Sharitt said:**
> Try 
```
sudo apt-get build-dep wesnoth
```
This should install all of the packages needed to build.

ok..done..
now i get this

```
marco@marco-laptop:/usr/src/wesnoth-1.4.5$ ./configure 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
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
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for ranlib... ranlib
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for XOpenDisplay in -lX11... yes
checking for pngmeta... no
checking for sdl-config... /usr/bin/sdl-config
checking for fribidi-config... /usr/bin/fribidi-config
checking for python... /usr/bin/python
checking Python version and location... /usr/bin/python, 2.5, /usr
checking whether Python is at least 2.4... yes
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
checking Python.h usability... yes
checking Python.h presence... yes
checking for Python.h... yes
checking for Py_Finalize in -lpython2.5... yes
checking for libpng-config... /usr/bin/libpng-config
checking for SDL - version >= 1.2.7... yes
checking for po4a... no
checking for asciidoc... no
checking for dos2unix... no
checking for xsltproc... /usr/bin/xsltproc
checking for libtool... no
checking for IMG_Load in -lSDL_image... yes
checking for Mix_OpenAudio in -lSDL_mixer... yes
checking for SDLNet_Init in -lSDL_net... yes
checking for freetype-config... /usr/bin/freetype-config
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking SDL.h usability... yes
checking SDL.h presence... yes
checking for SDL.h... yes
checking SDL_image.h usability... yes
checking SDL_image.h presence... yes
checking for SDL_image.h... yes
checking SDL_mixer.h usability... yes
checking SDL_mixer.h presence... yes
checking for SDL_mixer.h... yes
checking SDL_net.h usability... yes
checking SDL_net.h presence... yes
checking for SDL_net.h... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking sys/poll.h usability... yes
checking sys/poll.h presence... yes
checking for sys/poll.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for mode_t... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for error_at_line... yes
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for strftime... yes
checking for floor... no
checking for socket... yes
checking for strtoul... yes
checking for PNG support in SDL_image... yes
checking for OGG support in SDL_mixer... yes
checking for Boost headers version >= 1.33... no
configure: error: Could not find Boost headers version >= 1.33

```

---

### Post by malcolmx82 on 2008-11-10
no suggestions?

---

### Post by redilyn on 2008-11-10
I think you need to install the Boost headers.

Try this:

sudo apt-get install libboost-dev

Hope this helps

---

### Post by malcolmx82 on 2008-11-14
thank you..it works...

---

