---
title: "Usb-n13"
date: 2011-08-23
forum: Hardware
---

### Post by Ciscowolf on 2011-08-23
I am getting this Error code 2 at the end and I am just getting into linux and so far I am very pleased with it. I just need some help getting this USB wireless device to work before I can indulge my self more into Linux

Here is what I am getting on the Terminal. 

kristofer@Cisco-LIN:~$ cd desktop
bash: cd: desktop: No such file or directory
kristofer@Cisco-LIN:~$ cd Desktop
kristofer@Cisco-LIN:~/Desktop$ cd 2009
bash: cd: 2009: No such file or directory
kristofer@Cisco-LIN:~/Desktop$ cd 2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13
kristofer@Cisco-LIN:~/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$ sudo make
[sudo] password for kristofer: 
make -C tools
make[1]: Entering directory `/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools'
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools/bin2h
cp -f os/linux/Makefile.6 /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/Makefile
make  -C  /lib/modules/2.6.38-11-generic/build SUBDIRS=/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_md5.o
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.o
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.c:4002:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.c:4406:1: warning: the frame size of 1576 bytes is larger than 1024 bytes
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_wep.o
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/action.o
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_data.o
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.o
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.c:3709:2: error: implicit declaration of function ‘init_MUTEX’
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.c:3710:2: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/include/rtmp.h:5687:13: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
make[2]: *** [/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [LINUX] Error 2
kristofer@Cisco-LIN:~/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$

---

