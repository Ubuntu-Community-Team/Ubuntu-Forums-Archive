---
title: "URB_ASYNC_UNLINK error (compile USB Drivers COMTREND 350)"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by demons on 2006-10-29
Hello.
When i compile the USB driver (eagle-usb-2.3.2) for eagle's modem, shows this error.

checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for off_t... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for working volatile... yes
checking whether closedir returns void... no
checking whether gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking for sys/socket.h... (cached) yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking return type of signal handlers... void
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for strftime... yes
checking for alarm... yes
checking for gettimeofday... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strcspn... yes
checking for strdup... yes
checking for strerror... yes
checking for strncasecmp... yes
checking for strspn... yes
checking for strtol... yes
checking for ifconfig... yes
checking for route... yes
checking for pidof... yes
checking for dhclient... dhclient
checking for pppd... yes
checking for pppoe... yes
checking for tclsh... yes
checking for wish... yes
checking for xsltproc... yes
   *** libxslt-proc package is missing, keeping prebuild version ***
checking for kernel version... 2.6.15-26-386
checking for ifup... 1
checking for adictrl... no
checking for eaglectrl... no
checking for showstat... no
checking for eaglestat... no
checking for startadsl... no
checking for stopadsl... no
configure: creating ./config.status
config.status: creating Makefile.common
config.status: executing default commands

========================================================================
distribution detected                           Debian

dhcp support                                    dhclient

pppd support                                    yes
  pppoa support                                 yes
  pppoe support                                 yes

install eagleconnect (tcl/tk frontend)          yes

generate documentation                          no
========================================================================

/usr/src/eagle-usb-2.3.2$ sudo make
make -C drive
make[1]: se ingresa al directorio `/usr/src/eagle-usb-2.3.2/driver'

USE_CMVS=1 make  -C /lib/modules/2.6.15-26-386/build SUBDIRS=/usr/src/eagle-usb-2.3.2/driver modules

make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.15-26-386'

  CC [M]  /usr/src/eagle-usb-2.3.2/driver/eu_main.o

  CC [M]  /usr/src/eagle-usb-2.3.2/driver/eu_utils.o

  CC [M]  /usr/src/eagle-usb-2.3.2/driver/Pipes.o

/usr/src/eagle-usb-2.3.2/driver/Pipes.c: En la función ‘eu_write_completion’:
[b]
/usr/src/eagle-usb-2.3.2/driver/Pipes.c:922: error: ‘URB_ASYNC_UNLINK’ no se declaró aquí (primer uso en esta función)

/usr/src/eagle-usb-2.3.2/driver/Pipes.c:922: error: (Cada identificador no declarado solamente se reporta una vez

/usr/src/eagle-usb-2.3.2/driver/Pipes.c:922: error: para cada funcion en la que aparece.)

make[3]: *** [/usr/src/eagle-usb-2.3.2/driver/Pipes.o] Error 1

make[2]: *** [_module_/usr/src/eagle-usb-2.3.2/driver] Error 2

make[2]: se sale del directorio `/usr/src/linux-headers-2.6.15-26-386'

make[1]: *** [eagle-usb.ko] Error 2

make[1]: se sale del directorio `/usr/src/eagle-usb-2.3.2/driver'

make: *** [build] Error 2
[/b]

Can you help me with this
Thanks

---

