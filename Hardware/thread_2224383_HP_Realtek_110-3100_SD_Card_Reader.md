---
title: "HP Realtek 110-3100 SD Card Reader"
date: 2014-05-16
forum: Hardware
---

### Post by travis18 on 2014-05-16
I am a new user of Ubuntu. I have installed version 14.04 on my HP mini 110-3100CA netbook. All has been well except that I cannot get the drivers for the Realtek SD reader to install. I have read other posts with similar troubles but I have no success. Here is a copy of my terminal session. The make command seems to generate errors that I am not understanding. Thank you for any advice. 

kube@kube-HP:~$ cd /home/kube/Downloads/rts_pstor
kube@kube-HP:~/Downloads/rts_pstor$ make
sed "s/RTSX_MK_TIME/`date +%y.%m.%d.%H.%M`/" timestamp.in > timestamp.h
cp -f ./define.release ./define.h
make -C /lib/modules/3.13.0-24-generic/build/ SUBDIRS=/home/kube/Downloads/rts_pstor modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /home/kube/Downloads/rts_pstor/rtsx.o
/home/kube/Downloads/rts_pstor/rtsx.c:275:2: error: unknown field ‘proc_info’ specified in initializer
  .proc_info =   proc_info,
  ^
/home/kube/Downloads/rts_pstor/rtsx.c:275:2: warning: initialization from incompatible pointer type [enabled by default]
/home/kube/Downloads/rts_pstor/rtsx.c:275:2: warning: (near initialization for ‘rtsx_host_template.proc_dir’) [enabled by default]
/home/kube/Downloads/rts_pstor/rtsx.c:916:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtsx_probe’
 static int __devinit rtsx_probe(struct pci_dev *pci, const struct pci_device_id *pci_id)
                      ^
/home/kube/Downloads/rts_pstor/rtsx.c:1080:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtsx_remove’
 static void __devexit rtsx_remove(struct pci_dev *pci)
                       ^
/home/kube/Downloads/rts_pstor/rtsx.c:1106:11: error: ‘rtsx_probe’ undeclared here (not in a function)
  .probe = rtsx_probe,
           ^
/home/kube/Downloads/rts_pstor/rtsx.c:1107:2: error: implicit declaration of function ‘__devexit_p’ [-Werror=implicit-function-declaration]
  .remove = __devexit_p(rtsx_remove),
  ^
/home/kube/Downloads/rts_pstor/rtsx.c:1107:24: error: ‘rtsx_remove’ undeclared here (not in a function)
  .remove = __devexit_p(rtsx_remove),
                        ^
/home/kube/Downloads/rts_pstor/rtsx.c:485:12: warning: ‘rtsx_control_thread’ defined but not used [-Wunused-function]
 static int rtsx_control_thread(void * __dev)
            ^
/home/kube/Downloads/rts_pstor/rtsx.c:596:12: warning: ‘rtsx_polling_thread’ defined but not used [-Wunused-function]
 static int rtsx_polling_thread(void * __dev)
            ^
/home/kube/Downloads/rts_pstor/rtsx.c:745:13: warning: ‘quiesce_and_remove_host’ defined but not used [-Wunused-function]
 static void quiesce_and_remove_host(struct rtsx_dev *dev)
             ^
/home/kube/Downloads/rts_pstor/rtsx.c:780:13: warning: ‘release_everything’ defined but not used [-Wunused-function]
 static void release_everything(struct rtsx_dev *dev)
             ^
/home/kube/Downloads/rts_pstor/rtsx.c:790:12: warning: ‘rtsx_scan_thread’ defined but not used [-Wunused-function]
 static int rtsx_scan_thread(void * __dev)
            ^
/home/kube/Downloads/rts_pstor/rtsx.c:816:13: warning: ‘rtsx_init_options’ defined but not used [-Wunused-function]
 static void rtsx_init_options(struct rtsx_chip *chip)
             ^
cc1: some warnings being treated as errors
make[2]: *** [/home/kube/Downloads/rts_pstor/rtsx.o] Error 1
make[1]: *** [_module_/home/kube/Downloads/rts_pstor] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [default] Error 2
kube@kube-HP:~/Downloads/rts_pstor$

---

