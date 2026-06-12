---
title: "Problems installing the motorola sl modem in the new kernel"
date: 2008-06-18
forum: Hardware
---

### Post by cbarmpar on 2008-06-18
hi all,

I am trying to install the SM 56 PCI motorola modem modem in Ubuntu 8.04. I followed the relevant howto ([http://ubuntuforums.org/showthread.php?p=2756636](http://ubuntuforums.org/showthread.php?p=2756636)) but it didnt manage to install it. The only diference is that i am using the a diferent kernel from the one used in the tutorial.

The problem arises when I run the "make" command for the module. I recieve the following:

gramatia@gramatia-desktop:~/slmodem-2.9.11-20070505/drivers$ make
cc -I/lib/modules/2.6.24-18-generic/build/include -o kernel-ver kernel-ver.c
make all KERNEL_VER=2.6.24-18-generic
make[1]: Entering directory `/home/gramatia/slmodem-2.9.11-20070505/drivers'
make modules -C /lib/modules/2.6.24-18-generic/build SUBDIRS=/home/gramatia/slmodem-2.9.11-20070505/drivers
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
CC [M] /home/gramatia/slmodem-2.9.11-20070505/drivers/amrmo_init.o
/home/gramatia/slmodem-2.9.11-20070505/drivers/amrmo_init.c: &#931;&#964;&#951; &#963;&#965;&#957;&#940;&#961;&#964;&#951;&#963;&#951; ‘amrmo_pci_probe’:
/home/gramatia/slmodem-2.9.11-20070505/drivers/amrmo_init.c:620: &#963;&#966;&#940;&#955;&#956;&#945;: ‘SA_SHIRQ’ undeclared (first use in this function)
/home/gramatia/slmodem-2.9.11-20070505/drivers/amrmo_init.c:620: &#963;&#966;&#940;&#955;&#956;&#945;: (Each undeclared identifier is reported only once
/home/gramatia/slmodem-2.9.11-20070505/drivers/amrmo_init.c:620: &#963;&#966;&#940;&#955;&#956;&#945;: for each function it appears in.)
make[3]: *** [/home/gramatia/slmodem-2.9.11-20070505/drivers/amrmo_init.o] Error 1
make[2]: *** [_module_/home/gramatia/slmodem-2.9.11-20070505/drivers] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/gramatia/slmodem-2.9.11-20070505/drivers'
make: *** [all] Error 2

I think its because i am using the latest kernel. Is there anything we can do for that?

Many thanks in advance,
Regards,
Christos

---

