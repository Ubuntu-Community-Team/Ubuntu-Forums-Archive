---
title: "uncompressing linux error on ubuntu 6.06"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by manikantan_nambi on 2008-12-27
hi ,
Iam trying to install ubuntu 6.06 on my pc because the driver for a pci card that iam using supports only kernel 2.6.15.

so when i try to boot using live cd after mounting file system it just show Uncompressing linux... ok booting kernel and hangs there. i read on some of the forums that adding acpi = off in the boot solves the problem . but wen i do tat i get another error saying pnpbios fault and suggests to enter pnpbios = off.
i tried that too but it again it hangs at uncompressing linux.

here are my system specs.

Intel pentium dual core 2.00ghz
2gb ram
250 hdd
has windows vista installed

i tried installing it on a flash drive and it works fine. so is der a way to install linux to my hdd after booting from a flash drive. ???

i ve gone half crazy trying to make this work. plz help

---

### Post by wpshooter on 2008-12-27
Please explain in a little bit more detail what PCI card you are referring to and why it is that you would be limited to using Ubuntu 6.06.

Are you saying that the DRIVERS for your PCI device that are **_included in_** the more up to date versions of Ubuntu will not work with your PCI device ?  I find that a little hard to comprehend.

---

### Post by manikantan_nambi on 2008-12-27
iam using a sensoray data acquisition card 's626'. The drivers provided by them are only compatible with 2.6.15 kernel version. i tried compiling it with higher kernel versions but it gives me a long list of errors. and i am not that experienced to debug the driver. 

i tried it on another pc with ubuntu 6.06 and the driver works fine. so i thought of using 6.06. but i now iam unable to install it on this machine.  i even tried compiling only the kernel in ubuntu 8.04. but again i got some errors. i ll post the errors as soon as i can. 

but is there any way to get around this kernel loading problem ???

---

### Post by wpshooter on 2008-12-27
> **manikantan_nambi said:**
> iam using a sensoray data acquisition card 's626'. The drivers provided by them are only compatible with 2.6.15 kernel version. i tried compiling it with higher kernel versions but it gives me a long list of errors. and i am not that experienced to debug the driver. 

i tried it on another pc with ubuntu 6.06 and the driver works fine. so i thought of using 6.06. but i now iam unable to install it on this machine.  i even tried compiling only the kernel in ubuntu 8.04. but again i got some errors. i ll post the errors as soon as i can. 

but is there any way to get around this kernel loading problem ???

Are you positive that the higher versions of Ubuntu, Feisty, Gutsy, Hardy, & Intrepid, do not already contain drivers that will work with your card ?

---

### Post by manikantan_nambi on 2008-12-27
yes iam sure. i ve tried the newer versions. this is the error i get when i use 'make' in 8.10

root@ED209:/home/manikantan/Documents/s626_mar07# make
make -C /lib/modules/2.6.24-22-generic/build M=/home/manikantan/Documents/s626_mar07 SUBDIRS=/home/manikantan/Documents/s626_mar07
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
  LD      /home/manikantan/Documents/s626_mar07/built-in.o
  CC [M]  /home/manikantan/Documents/s626_mar07/s626drv.o
/home/manikantan/Documents/s626_mar07/s626drv.c:64:26: error: linux/config.h: No such file or directory
/home/manikantan/Documents/s626_mar07/s626drv.c: In function 'S626_init':
/home/manikantan/Documents/s626_mar07/s626drv.c:777: error: implicit declaration of function 'pci_module_init'
/home/manikantan/Documents/s626_mar07/s626drv.c: In function 'S626DRV_RequestIRQ':
/home/manikantan/Documents/s626_mar07/s626drv.c:948: error: 'SA_SHIRQ' undeclared (first use in this function)
/home/manikantan/Documents/s626_mar07/s626drv.c:948: error: (Each undeclared identifier is reported only once
/home/manikantan/Documents/s626_mar07/s626drv.c:948: error: for each function it appears in.)
/home/manikantan/Documents/s626_mar07/s626drv.c:953: warning: passing argument 2 of 'request_irq' from incompatible pointer type
make[2]: *** [/home/manikantan/Documents/s626_mar07/s626drv.o] Error 1
make[1]: *** [_module_/home/manikantan/Documents/s626_mar07] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make: *** [all] Error 2

---

