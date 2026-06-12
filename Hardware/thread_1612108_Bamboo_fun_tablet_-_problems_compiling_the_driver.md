---
title: "Bamboo fun tablet - problems compiling the driver"
date: 2010-11-02
forum: Hardware
---

### Post by bardes on 2010-11-02
I've been trying to compile the driver for hours but the wacom.ko file just refuses to appear :mad:. I've followed more than 5 tutorials and got the same problem in all of them: the cp command never founded the wacom.ko file

I'm running ubuntu 10.04 64 bits and according to uname -r my kernel is 2.6.32-25-generic.

BTW, my evdev_drv.so is located in here: /usr/lib/xorg/modules/input/evdev_drv.so so the configure flag is not the problem...

any help is welcome :)

---

### Post by Favux on 2010-11-02
Can you post the output of your ./configure?

---

### Post by bardes on 2010-11-02
Sure, here it is:
```
paulo@paulo-laptop:~$ cd Desktop/linuxwacom-0.8.8-10/
paulo@paulo-laptop:~/Desktop/linuxwacom-0.8.8-10$ ./configure --enable-wacom --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) gawk
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for HAL... yes
checking for arch type... x86_64-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.32-25-generic/build
checking kernel version... 2.6.32-25-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Xorg server is version 1.4 or later... yes
checking if Xorg is 7.3 or earlier... no
checking if Xorg server is version 1.5.2 or later... yes
checking if Xorg server is version 1.6 or later... yes
checking if Xorg server is version 1.7 or later... yes
checking if Xorg SDK defined IsXExtensionPointer... yes
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
checking if wacomxrrd should be built... checking X11/extensions/Xrandr.h usability... yes
checking X11/extensions/Xrandr.h presence... yes
checking for X11/extensions/Xrandr.h... yes
yes
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
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.30/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: creating src/include/kernel-config.h
config.status: creating src/include/util-config.h
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.30
      kernel source - yes /lib/modules/2.6.32-25-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - no 
             xidump - no 
        libwacomcfg - no
         libwacomxi - no
          xsetwacom - no
          wacomxrrd - no
              hid.o - no 
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - hal IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.32-25-generic/build M=/home/paulo/Área de Trabalho/linuxwacom-0.8.8-10/src/2.6.30
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
make[1]: *** No rule to make target `de'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [all] Error 2


Your wacom.ko is available under 
    /home/paulo/Desktop/linuxwacom-0.8.8-10/src/2.6.30


NOTE: the X driver in this package only supports Xorg servers older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.
The kernel driver provided in this package is independent of 
the X server version

paulo@paulo-laptop:~/Desktop/linuxwacom-0.8.8-10$ 
```

this is what I got with the linuxwacom-0.8.8-10 version.

---

### Post by Favux on 2010-11-02
Well it looks OK so far.

Under "BUILD OPTIONS:" it says it will build the wacom.ko 'wacom.o - yes'.  And it tells you:
"Your wacom.ko is available under 
    /home/paulo/Desktop/linuxwacom-0.8.8-10/src/2.6.30"

So that's where it should be unless there's an error in 'make'.  What's your 'make' output look like?

---

### Post by bardes on 2010-11-03
I think the problem is during the make. Here is what I got:

```
paulo@paulo-laptop:~/Desktop/linuxwacom-0.8.8-10$ make
Making all in src
make[1]: Entrando no diretório `/home/paulo/Área de Trabalho/linuxwacom-0.8.8-10/src'
Making all in 2.6.30
make[2]: Entrando no diretório `/home/paulo/Área de Trabalho/linuxwacom-0.8.8-10/src/2.6.30'
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.32-25-generic/build M=/home/paulo/Área de Trabalho/linuxwacom-0.8.8-10/src/2.6.30
make[3]: Entrando no diretório `/usr/src/linux-headers-2.6.32-25-generic'
make[3]: *** Sem regra para processar o alvo `de'.  Pare.
make[3]: Saindo do diretório `/usr/src/linux-headers-2.6.32-25-generic'
make[2]: ** [all] Erro 2
make[2]: Saindo do diretório `/home/paulo/Área de Trabalho/linuxwacom-0.8.8-10/src/2.6.30'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/paulo/Área de Trabalho/linuxwacom-0.8.8-10/src'
make: ** [all-recursive] Erro 1
paulo@paulo-laptop:~/Desktop/linuxwacom-0.8.8-10$
```

Also during the ./configure it said:

make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
make[1]: *** No rule to make target `de'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [all] Error 2

Looks like some problem, but I have no idea what it is... :(

---

### Post by Favux on 2010-11-03
Yes the problem is with 'make'.  When it says 'Error 2' you're in trouble.

I don't know what `de' is.  Usually it's more descriptive like modules or install or a directory path or something.

Let's just assume you haven't installed the correct kernel headers because it is happening in /usr/src/linux-headers-2.6.32-25-generic.  What kernel do you have?:
```
uname -r
```
If it's the generic then run:
```
sudo apt-get install linux-headers-generic
```
and redo.  Before running ./configure, after you're in the source code directory, run 'make clean'.

---

### Post by bardes on 2010-11-03
Yay, I discovered what was wrong. The folder was in my desktop and it should (read must) be in the home folder to compile right. I've moved it and now it compiled fine, I got the wacom.ko file but now I don't know exactly what I have to do...

I saw some tutorial saying that I have to move it to  /lib/modules/`uname -r`/kernel/drivers/input/tablet/

I did it:
```

paulo@paulo-laptop:~/linuxwacom-0.8.8-10/src/2.6.30$ sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/
[sudo] password for paulo: 
paulo@paulo-laptop:~/linuxwacom-0.8.8-10/src/2.6.30$ sudo rmmod wacom
ERROR: Module wacom does not exist in /proc/modules
paulo@paulo-laptop:~/linuxwacom-0.8.8-10/src/2.6.30$ sudo modprobe wacom
paulo@paulo-laptop:~/linuxwacom-0.8.8-10/src/2.6.30$ 

```

But nothing happened :confused:. Any idea why?

---

### Post by Favux on 2010-11-03
In the source code tarball directory I would use:
```
sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
followed by:
```
sudo depmod -a
```
and a reboot.  Rebooting works better, I don't know why.  Sometimes you need to do it a couple of times for things to "shake out".

See the Bamboo P&T HOW TO:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

---

### Post by bardes on 2010-11-03
Ok, I'll try it right now :)

---

### Post by bardes on 2010-11-03
BTW, It would be a good idea to change it in the tutorial, because the only problem during the make was the location of the source code folder...

---

### Post by Favux on 2010-11-03
Hi bardes,

I don't think that was the problem.  Originally you showed:
```
paulo@paulo-laptop:~$ cd Desktop/linuxwacom-0.8.8-10/

```
You need to explain what this is about:
```
/home/paulo/Área de Trabalho/linuxwacom-0.8.8-10/src
```
Because in a linux directory you can't have spaces in a directory path, 'Área de Trabalho'.  That is not valid in a directory.

---

### Post by bardes on 2010-11-03
Yay it's working beautifully\\:D/ Thanks a lot for your attention and help. (And also for the tutorial)

Just a last question how do I customize the buttons?

---

### Post by Favux on 2010-11-03
Great!  :)

Also in the tutorial.  Step IV and the xsetwacom script.

---

### Post by bardes on 2010-11-03
Ok, thanks again for the help. About the file location, it was fault of the translation. In the pt-br version of ubuntu, the Desktop folder is by default called "Área de Trabalho" to work around this I've made a symbolic link to "Área de Trabalho" with the name of "Desktop".

This invalid name to the desktop is a very stupid problem that have already given me other headaches before. :mad:

Any ways, thanks very much :P:P:P

---

### Post by Favux on 2010-11-03
You're welcome.  Glad you are set up.  :)

> About the file location, it was fault of the translation. In the pt-br version of ubuntu, the Desktop folder is by default called "Área de Trabalho" to work around this I've made a symbolic link to "Área de Trabalho" with the name of "Desktop".
Ahhh.  And pt-br is Portuguese-Brazilian?

---

### Post by bardes on 2010-11-03
yep.

BTW wacom should be thankful to you, I think I saw posts form you in all threads about it, and without you me and lots of other people would never set it up in ubuntu ;)

---

### Post by Favux on 2010-11-03
No free Cintiq or Intuos4 yet.  :(

---

### Post by bardes on 2010-11-03
Lol that would be a nice pay back ^^

Just to prove that everything is perfect:
[IMG]http://img169.imageshack.us/img169/5782/thanksmy.png[/IMG]

---

