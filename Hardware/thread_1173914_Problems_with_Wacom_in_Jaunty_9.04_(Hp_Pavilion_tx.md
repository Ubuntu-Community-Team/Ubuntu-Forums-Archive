---
title: "Problems with Wacom in Jaunty 9.04 (Hp Pavilion tx2075BR)"
date: 2009-05-30
forum: Hardware
---

### Post by Arajabat on 2009-05-30
Hello there.

I have a HP Pavilion tx2075BR, and recently installed Ubuntu on it. Since then, I'm trying to get my Wacom working, with little sucess.

My last attempt regarding this matter was following this thread instructions

[http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

But I'm having some problems with Step 5 in it. I simply can't compile the driver. I'm getting this output message when I run make:

Note: My Ubuntu is in Portuguese. For those who not speek Portuguese (Almost everyone, I guess), the translations of the portuguese terms in the message are listed below. Sorry for that >.<

Entrando no diretório:  Going into directory
Nada a ser feito: Nothing to be done
Saindo do diretório: Exiting the directory
Arquivo ou diretório inexistente: File or directory doesn't exist

```

Making all in src
make[1]: Entrando no diretório `/home/cake/Desktop/linuxwacom-0.8.2-2/src'
Making all in .
make[2]: Entrando no diretório `/home/cake/Desktop/linuxwacom-0.8.2-2/src'
make[2]: Nada a ser feito para `all-am'.
make[2]: Saindo do diretório `/home/cake/Desktop/linuxwacom-0.8.2-2/src'
Making all in wacomxi
make[2]: Entrando no diretório `/home/cake/Desktop/linuxwacom-0.8.2-2/src/wacomxi'
make[2]: Nada a ser feito para `all'.
make[2]: Saindo do diretório `/home/cake/Desktop/linuxwacom-0.8.2-2/src/wacomxi'
Making all in util
make[2]: Entrando no diretório `/home/cake/Desktop/linuxwacom-0.8.2-2/src/util'
make[2]: Nada a ser feito para `all'.
make[2]: Saindo do diretório `/home/cake/Desktop/linuxwacom-0.8.2-2/src/util'
Making all in xdrv
make[2]: Entrando no diretório `/home/cake/Desktop/linuxwacom-0.8.2-2/src/xdrv'
gcc -g -O2 -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \
        -pedantic -Wall -Wpointer-arith -fno-merge-constants \
        -fno-stack-protector -I. -I../include -I/usr/include/xorg  \
         -I/usr/include/xorg -I/usr/include/pixman-1   \
        -o xf86Wacom.o -c ./xf86Wacom.c
In file included from ./xf86Wacom.c:84:
./xf86Wacom.h:30:28: error: xf86Version.h: Arquivo ou diretório inexistente
make[2]: ** [xf86Wacom.o] Erro 1
make[2]: Saindo do diretório `/home/cake/Desktop/linuxwacom-0.8.2-2/src/xdrv'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/cake/Desktop/linuxwacom-0.8.2-2/src'
make: ** [all-recursive] Erro 1

```Also, below is the output that I get when I run the ./configure

```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gawk... (cached) gawk
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
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for arch type... i486-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.28-11-generic/build
checking kernel version... 2.6.28-11-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Uninit is called... yes
checking if Xorg is version 1.6 or later... yes
checking if Xorg SDK defines IsXExtensionPointer... yes
checking if Xorg SDK defines dixScreenOrigins... yes
checking XInput extension version... >= 2.0
checking for lib xf86config... checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... found, /usr/include/tcl8.4
checking for tk header files... found, /usr/include/tcl8.4
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... yes
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... yes
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.4/Makefile
config.status: creating src/2.4.22/Makefile
config.status: creating src/2.6.8/Makefile
config.status: creating src/2.6.9/Makefile
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/2.6.22/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.26/Makefile
config.status: creating src/2.6.27/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: src/include/xdrv-config.h is unchanged
config.status: creating src/include/kernel-config.h
config.status: src/include/kernel-config.h is unchanged
config.status: creating src/include/util-config.h
config.status: src/include/util-config.h is unchanged
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.27
  module versioning - no 
      kernel source - yes /lib/modules/2.6.28-11-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - no
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
         usbmouse.o - no
            evdev.o - no
         mousedev.o - no
            input.o - no
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - Uninit-called IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------

```Thank all of you in advance. And sorry if there are some awful errors in the text, english is not my native language (as you may have guessed).

---

### Post by Favux on 2009-05-30
Hi Arajabat,

Welcome to Ubuntu!

The problem is most likely that linuxwacom 0.8.2-2 does not support the Xserver 1.6 that comes with Jaunty.  The linuxwacom 0.8.3-2 is the first to support Xserver 1.6.

While Synaptics Package Manager will tell you linuxwacom 0.8.2-2 is installed in Jaunty it is a special version.  It has been patched to work on Xserver 1.6 and work with HAL.

What you want to do is read **Jaunty Users** near the top of the HOW TO and then go to gali98's HOW TO (linked in 1) on post #104.  There you will use the 0.8.3-4 wacom.ko with the "native" Jaunty 0.8.2-2 packages.  You will also add a new wacom.fdi and suspension script.  I will also link to the new HOW TO here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)

Good luck!

PS:  The English in your post was well done.

---

### Post by Arajabat on 2009-05-30
Wow! Thank you a lot, it is working now.

Only a little question... The button in the pen isn't working. Should it be working by now, or do I have to make something else to make it work?

---

### Post by Favux on 2009-05-30
Hi Arajabat,

Outstanding!  Nice job.

The stylus button can be configured with wacomcpl.  To use wacomcpl see Section 3 in the HOW TO you were originally using (page 1, post 1).  If you want it to be a right mouse click in stylus tell Button2 to be 3.  2 is the middle mouse click.

---

### Post by Arajabat on 2009-05-31
Hmm... I used wacomcpl to set button 2 to the right mouse button, but it still didn't work (Actually, it seems that it's not working with any button that I set)

---

### Post by Favux on 2009-05-31
Hi Arajabat,

Well that isn't right.  To rule out a hardware problem does the stylus button work in Windows.  If it does maybe you can post your .xinitrc?

---

### Post by Arajabat on 2009-05-31
It's working well in Windows. My .xinitrc file is

```

xsetwacom set touch bottomy "3933"
xsetwacom set touch bottomx "4017"
xsetwacom set touch topy "200"
xsetwacom set touch topx "149"
xsetwacom set stylus Suppress "2"
xsetwacom set stylus RawSample "4"
xsetwacom set stylus ClickForce "6"
xsetwacom set stylus PressCurve "0 0 100 100"
xsetwacom set eraser bottomy "16399"
xsetwacom set eraser bottomx "26302"
xsetwacom set eraser topy "103"
xsetwacom set eraser topx "52"
xsetwacom set stylus bottomy "16399"
xsetwacom set stylus bottomx "26302"
xsetwacom set stylus topy "103"
xsetwacom set stylus topx "52"
xsetwacom set stylus TPCButton "on"
xsetwacom set stylus Button3 "Button 0"
xsetwacom set stylus Button2 "Button 3"
xsetwacom set stylus Button1 "Button 1"
# run the primary system script
. /etc/X11/xinit/xinitrc

```

---

### Post by Favux on 2009-05-31
Hi Arajabat,

I don't see anything wrong with your .xinitrc.  Are you pressing the side switch when your stylus tip is in contact with the glass?  That's how most folks set it up.  In wacomcpl when you've selected it options pop up.  One is "Side Switch Mode" and I have selected "Side Switch + Tip" but you can have "Side Switch Only"

---

### Post by Arajabat on 2009-06-01
Wow, thank you. It work now!

---

### Post by Favux on 2009-06-01
Hi Arajabat,

Good deal.  You're welcome.

---

