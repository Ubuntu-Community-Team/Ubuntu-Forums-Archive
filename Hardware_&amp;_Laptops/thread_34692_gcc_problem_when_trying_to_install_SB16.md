---
title: "gcc problem when trying to install SB16"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by 4ebees on 2005-05-16
Hi,

I've been having soundcard problems.

I'm using a Compaq Deskpro.

I've installed a SoundBlaster16 card - I couldn't get the es19xx card to run at all.

Now, when I try to install the alsa driver I get the following:

**************************
judith@ubuntu:/usr/src/alsa/alsa-driver-1.0.9rc3 $ ./configure --with-cards=sb16 --with-sequencer=yes;make;make install
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.9rc3
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9rc3'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc3'

Please, run the configure script as first...

rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9rc3/acore'
Makefile:6: /usr/src/alsa/alsa-driver-1.0.9rc3/Makefile.conf: No such file or directory
make[1]: *** No rule to make target `/usr/src/alsa/alsa-driver-1.0.9rc3/Makefile.conf'.  Stop.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc3/acore'
make: *** [install-modules] Error 1
judith@ubuntu:/usr/src/alsa/alsa-driver-1.0.9rc3 $ sudo ./configure --with-cards=sb16 --with-sequencer=yes;make;make install
Password:
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.9rc3
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9rc3'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc3'

Please, run the configure script as first...

rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9rc3/acore'
Makefile:6: /usr/src/alsa/alsa-driver-1.0.9rc3/Makefile.conf: No such file or directory
make[1]: *** No rule to make target `/usr/src/alsa/alsa-driver-1.0.9rc3/Makefile.conf'.  Stop.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc3/acore'
make: *** [install-modules] Error 1

************************

Any assistance or advice would be most appreciated.

Thanks.
Patrick

---

### Post by nad on 2005-05-16
gcc is telling you that in order to compile this code it needs a configure script.

From within the source directory, issue the command: ./configure

and now make and make install .

Or, all on one line: ./configure && make && make install  (as root of course)

---

