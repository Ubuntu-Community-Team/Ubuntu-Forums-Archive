---
title: "header problems installing slmodem"
date: 2008-08-27
forum: General Help
---

### Post by KenSpeedie on 2008-08-27
I am attempting to install slmodem fax modem.

I found a post on how to install this modem.

Where I get into trouble is with linux headers.

Post says do # make clean first, then # make.

No problem with # make clean

(Shouldn't make clean come AFTER make?)

When I do # make I get 

make -C modem clean &&  make -C drivers clean &&  echo "done."
make[1]: Entering directory `/home/ken/download/tar/slmodem-2.9.11-20080817/modem'
rm -f slmodemd modem_test modem_main.o modem_cmdline.o modem_test.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o sysdep_common.o
rm -f *~ *.orig *.rej
make[1]: Leaving directory `/home/ken/download/tar/slmodem-2.9.11-20080817/modem'
make[1]: Entering directory `/home/ken/download/tar/slmodem-2.9.11-20080817/drivers'
rm -f kernel-ver slamr.o  slusb.o  slamr.ko slusb.ko *st7554.o amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~
rm -f -r .tmp_versions
make[1]: Leaving directory `/home/ken/download/tar/slmodem-2.9.11-20080817/drivers'
done.
ken@ken-desktop:~/download/tar/slmodem-2.9.11-20080817$ sudo make
make -C modem all
make[1]: Entering directory `/home/ken/download/tar/slmodem-2.9.11-20080817/modem'
rebuild profile...
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_main.o -c modem_main.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_cmdline.o -c modem_cmdline.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem.o -c modem.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_datafile.o -c modem_datafile.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_at.o -c modem_at.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_timer.o -c modem_timer.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_pack.o -c modem_pack.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_ec.o -c modem_ec.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_comp.o -c modem_comp.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_param.o -c modem_param.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_debug.o -c modem_debug.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o homolog_data.o -c homolog_data.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o dp_sinus.o -c dp_sinus.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o dp_dummy.o -c dp_dummy.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o sysdep_common.o -c sysdep_common.c
gcc -o slmodemd modem_main.o modem_cmdline.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_test.o -c modem_test.c
gcc -o modem_test modem_test.o modem_cmdline.o modem.o modem_datafile.o modem_at.o modem_timer.o modem_pack.o modem_ec.o modem_comp.o modem_param.o modem_debug.o homolog_data.o dp_sinus.o dp_dummy.o dsplibs.o sysdep_common.o
make[1]: Leaving directory `/home/ken/download/tar/slmodem-2.9.11-20080817/modem'
make -C drivers KERNEL_DIR=/lib/modules/2.6.15-52-386/build
make[1]: Entering directory `/home/ken/download/tar/slmodem-2.9.11-20080817/drivers'
doing kernel-ver::
cc -I/lib/modules/2.6.15-52-386/build/include -o kernel-ver kernel-ver.c
make all KERNEL_VER=2.6.11
make[2]: Entering directory `/home/ken/download/tar/slmodem-2.9.11-20080817/drivers'
        obj-m=slamr.o  slusb.o
        slamr-objs=amrmo_init.o sysdep_amr.o amrlibs.o
make modules -C /lib/modules/2.6.15-52-386/build SUBDIRS=/home/ken/download/tar/slmodem-2.9.11-20080817/drivers
make: Entering an unknown directory
make: *** /lib/modules/2.6.15-52-386/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/ken/download/tar/slmodem-2.9.11-20080817/drivers'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/ken/download/tar/slmodem-2.9.11-20080817/drivers'
make: *** [drivers] Error 2

Everyting is fine until we get to 

make -C drivers KERNEL_DIR=/lib/modules/2.6.15-52-386/build

Which does not exist.

We also get: make: *** /lib/modules/2.6.15-52-386/build: No such file or directory.

Post also says use the link:

ln -s /usr/src/linux-headers-2.6.8.1-4-686 /lib/modules/2.6.8.1-4-686/build

Replaceing the version number with my kernal does not work because the only thing in /usr/src is rpm

Next step is to do # make install  KERNEL_VER=`uname -r`

That does not work because  # make failed.

I know the trouble is with the "path to kernal", but I am not sure what to do about it.

Thanks for your help.

---

