---
title: "Enabling a MTP Device"
date: 2009-04-12
forum: Hardware
---

### Post by Kingy_0 on 2009-04-12
Hello all I hope I'm posting this topic in the right part of the forums. 

I'm new to Ubuntu & GNU/Linux in general and a bit unused to the more technical elements involved with it. Unfortunately I'm having a problem trying to install the latest version of libmtp from their website at sourceforge: [here]("http://libmtp.sourceforge.net/")

I removed the current version I had installed of MTP which by default was:

*Package:* libmtp8

*Installed Version:* 0.3.0

**and I kept the current version of libusb installed** The version of libusb I'm supposed to have installed:

*Package:* libusb-0.1-4

*Installed Version:* 0.1.12

^The above information is according to Synaptic^

I've extracted the tarball and ran the installer but it cannot seem to find libusb, which is strange because it is installed by default according to Synaptic. Unfortunately because I'm new to Ubuntu the installer has thrown up a rather cryptic error message (cryptic at least to me) I've copied & pasted it below:

> Kingy@ubuntu:~/Desktop$ ./configure
bash: ./configure: No such file or directory
Kingy@ubuntu:~/Desktop$ cd /home/Kingy/Desktop/libmtp-0.3.6
Kingy@ubuntu:~/Desktop/libmtp-0.3.6$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
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
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
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
appending configuration tag "F77" to libtool
checking for doxygen... false
configure: WARNING: *** doxygen not found, docs will not be built
checking if the host operating system is Darwin... no
checking For MinGW32... no
checking for usb_control_msg in -lusb... no
configure: error: I can't find the libusb libraries on your system. You
	may need to set the LDFLAGS environment variable to include the
	search path where you have libusb installed before running
	configure (e.g. setenv LDFLAGS=-L/usr/local/lib)


Sorry for the rather lengthy error message but after reading the message again I thought I may have some discrepancies with the packages I have installed, may need to install additional packages as well as finding the location of the hidden libusb.

Could somebody please point me in the right direction. Would be much appreciated thanks!

-Kingy_0- ):P

---

