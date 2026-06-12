---
title: "installing smart link faxmodem"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by yyagol on 2005-07-28
Hi every1
i am new to ubuntu/ befor i used Fedora and RedHat
but i must say UBUNTU is the best 1 i ever used.
the problem i have is to install my fax modem
i download the original driver from the smart link site
and when i try to install i get this error:
```
$ make
make -C modem all
make[1]: Entering directory `/home/yyagol/Downloads/slmodem-2.9.10/modem'
rebuild profile...
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_main.o -c modem_main.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_cmdline.o -c modem_cmdline.cgcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem.o -c modem.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_datafile.o -c modem_datafile.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_at.o -c modem_at.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_timer.o -c modem_timer.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_pack.o -c modem_pack.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_ec.o -c modem_ec.c
modem_ec.c:689: warning: `t403_timeout' defined but not used
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_comp.o -c modem_comp.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_param.o -c modem_param.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_debug.o -c modem_debug.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o homolog_data.o -c homolog_data.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o dp_sinus.o -c dp_sinus.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o dp_dummy.o -c dp_dummy.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o sysdep_common.o -c sysdep_common.cgcc -o slmodemd modem_main.o modem_cmdline.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_test.o -c modem_test.c
gcc -o modem_test modem_test.o modem_cmdline.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o
make[1]: Leaving directory `/home/yyagol/Downloads/slmodem-2.9.10/modem'
``` 
then i try to install:
```
$ sudo make install
Password:
make -C modem all
make[1]: Entering directory `/home/yyagol/Downloads/slmodem-2.9.10/modem'
make[1]: Leaving directory `/home/yyagol/Downloads/slmodem-2.9.10/modem'
make -C drivers KERNEL_DIR=/lib/modules/2.6.10-5-386/build
make[1]: Entering directory `/home/yyagol/Downloads/slmodem-2.9.10/drivers'
cc -I/lib/modules/2.6.10-5-386/build/include -o kernel-ver kernel-ver.c
make all KERNEL_VER=2.6.0-test7
make[2]: Entering directory `/home/yyagol/Downloads/slmodem-2.9.10/drivers'
make modules -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/yyagol/Downloads/slmodem-2.9.10/drivers
make: *** /lib/modules/2.6.10-5-386/build: No such file or directory.  Stop.
make: Entering an unknown directorymake: Leaving an unknown directorymake[2]: *** [all] Error 2
make[2]: Leaving directory `/home/yyagol/Downloads/slmodem-2.9.10/drivers'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/yyagol/Downloads/slmodem-2.9.10/drivers'
make: *** [drivers] Error 2
``` 

can some 1 please :confused:  tel me what is wrong hear?

---

### Post by elfgoh on 2005-10-19
You need to install the linux headers

---

