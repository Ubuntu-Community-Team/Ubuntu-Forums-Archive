---
title: "Laptop Modem won't install"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by lillypilly on 2007-04-15
I am trying to get the modem working on my laptop. It is a softmodem. I have tried several time to get this working.

The details of the modem which shows on Windows as being a Smartlink 56 are

=====================================================================

=              SYSTEM INFORMATION                                   =

=====================================================================

Date         : 4/15/2007

ListMdm Ver  : 1.6

Windows OS   : Microsoft Windows XP 

Build Number : 2600 



=====================================================================

=              RESULT OF MODEM QUERY                                =

=====================================================================

NUMBER OF MODEMS FOUND = 1



MODEM #1:

  PCI CONFIGURATION INFORMATION READ:

     VENDOR ID              : 8086

     DEVICE ID              : 24D6

     SUBVENDOR ID           : 1558

     SUBDEVICE ID           : 0800

     REVISION ID            : 02



  DEDUCED INFORMATION:

     VENDOR NAME            : ICH

     DEVICE NAME            : ICH5 (AC '97 MODEM)

     SUBVENDOR NAME         : UNKNOWN

     MODEM TYPE             : HSF

     WINXP INBUILD SUPPORT  : NO



When I try to install the modem I note the following details when I run "make" and "make install"



username:~/a$ cd slmodem

username:~/a/slmodem$ make

make -C modem all
make[1]: Entering directory `/home/username/a/slmodem/modem'
rebuild profile...
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_main.o -c modem_main.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_cmdline.o -c modem_cmdline.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem.o -c modem.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_datafile.o -c modem_datafile.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_at.o -c modem_at.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_timer.o -c modem_timer.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_pack.o -c modem_pack.c
modem_pack.c: In function ‘modem_async_get_bits’:
modem_pack.c:100: warning: pointer targets in passing argument 2 of ‘m->get_chars’ differ in signedness
modem_pack.c: In function ‘modem_async_put_bits’:
modem_pack.c:148: warning: pointer targets in passing argument 2 of ‘m->put_chars’ differ in signedness
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_ec.o -c modem_ec.c
modem_ec.c: In function ‘tx_info’:
modem_ec.c:723: warning: pointer targets in passing argument 2 of ‘l->modem->get_chars’ differ in signedness
modem_ec.c: In function ‘push_rest_data’:
modem_ec.c:811: warning: pointer targets in passing argument 2 of ‘l->modem->put_chars’ differ in signedness
modem_ec.c: In function ‘rx_info’:
modem_ec.c:860: warning: pointer targets in passing argument 2 of ‘l->modem->put_chars’ differ in signedness
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_comp.o -c modem_comp.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_param.o -c modem_param.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_debug.o -c modem_debug.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o homolog_data.o -c homolog_data.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o dp_sinus.o -c dp_sinus.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o dp_dummy.o -c dp_dummy.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o sysdep_common.o -c sysdep_common.c
gcc  -o slmodemd modem_main.o modem_cmdline.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_test.o -c modem_test.c
gcc  -o modem_test modem_test.o modem_cmdline.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o
make[1]: Leaving directory `/home/username/a/slmodem/modem'
make -C drivers KERNEL_DIR=/lib/modules/2.6.20-15-generic/build
make[1]: Entering directory `/home/username/a/slmodem/drivers'
cc -I/lib/modules/2.6.20-15-generic/build/include -o kernel-ver kernel-ver.c
make all KERNEL_VER=2.6.20-15-generic
make[2]: Entering directory `/home/username/a/slmodem/drivers'
make modules -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/username/a/slmodem/drivers
make[3]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/username/a/slmodem/drivers/amrmo_init.o
/home/username/a/slmodem/drivers/amrmo_init.c:46:26: error: linux/config.h: No such file or directory
/home/username/a/slmodem/drivers/amrmo_init.c: In function ‘amrmo_pci_probe’:
/home/username/a/slmodem/drivers/amrmo_init.c:589: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[4]: *** [/home/username/a/slmodem/drivers/amrmo_init.o] Error 1
make[3]: *** [_module_/home/username/a/slmodem/drivers] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/username/a/slmodem/drivers'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/username/a/slmodem/drivers'
make: *** [drivers] Error 2


username:~/a/slmodem$ make install


make -C modem all
make[1]: Entering directory `/home/username/a/slmodem/modem'
make[1]: Leaving directory `/home/username/a/slmodem/modem'
make -C drivers KERNEL_DIR=/lib/modules/2.6.20-15-generic/build
make[1]: Entering directory `/home/username/a/slmodem/drivers'
cc -I/lib/modules/2.6.20-15-generic/build/include -o kernel-ver kernel-ver.c
make all KERNEL_VER=2.6.20-15-generic
make[2]: Entering directory `/home/username/a/slmodem/drivers'
make modules -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/username/a/slmodem/drivers
make[3]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/username/a/slmodem/drivers/amrmo_init.o
/home/username/a/slmodem/drivers/amrmo_init.c:46:26: error: linux/config.h: No such file or directory
/home/username/a/slmodem/drivers/amrmo_init.c: In function ‘amrmo_pci_probe’:
/home/username/a/slmodem/drivers/amrmo_init.c:589: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[4]: *** [/home/username/a/slmodem/drivers/amrmo_init.o] Error 1
make[3]: *** [_module_/home/username/a/slmodem/drivers] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/username/a/slmodem/drivers'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/username/a/slmodem/drivers'
make: *** [drivers] Error 2

I also note in the when I look in the  /dev directory that there are tty files from 0 to 31 and ttya1 to ttyzf with many numbers

I don't know what I am doing wrong as I have read as many "How to's" and questions on this site as I can possiblely find.

---

### Post by Matchless on 2007-04-15
HSF modem is a Conexant and drivers are only available from Linuxant. Just to be sure download their free driver that is locked to 14400k and test. if this works then you can decide on paying them a fee for a registration code to open up the driver to 56k

---

