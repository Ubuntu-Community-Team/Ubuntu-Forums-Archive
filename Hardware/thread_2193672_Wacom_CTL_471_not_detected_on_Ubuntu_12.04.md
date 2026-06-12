---
title: "Wacom CTL 471 not detected on Ubuntu 12.04"
date: 2013-12-14
forum: Hardware
---

### Post by nath-nilanjan on 2013-12-14
Hello,

I followed a previous [post]("http://ubuntuforums.org/showthread.php?t=1951073") and tried to install a Wacom CTL-471 (new entry level model launched in India by name of One).

While installing Wacom 
[FONT=courier new]sudo apt-get install wacom-dkms[/FONT]

Got the following error:
   [FONT=courier new]Error! Bad return status for module build on kernel: 3.8.0-34-generic (x86_64)  
[/FONT]
[FONT=courier new]Consult /var/lib/dkms/wacom/0.13.0/build/make.log for more information.[/FONT]

Here is the output of the log file.
[FONT=courier new]DKMS make.log for wacom-0.13.0 for kernel 3.8.0-34-generic (x86_64)
Sat Dec 14 12:16:33 IST 2013
    Building input-wacom drivers for 2.6 kernel.
make -C /lib/modules/3.8.0-34-generic/build M=/var/lib/dkms/wacom/0.13.0/build
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-34-generic'
  LD      /var/lib/dkms/wacom/0.13.0/build/built-in.o
  CC [M]  /var/lib/dkms/wacom/0.13.0/build/wacom_wac.o
/var/lib/dkms/wacom/0.13.0/build/wacom_wac.c: In function &#8216;wacom_pl_irq&#8217;:
/var/lib/dkms/wacom/0.13.0/build/wacom_wac.c:79:3: error: implicit declaration of function &#8216;dbg&#8217; [-Werror=implicit-function-declaration]
/var/lib/dkms/wacom/0.13.0/build/wacom_wac.c: In function &#8216;wacom_setup_input_capabilities&#8217;:
/var/lib/dkms/wacom/0.13.0/build/wacom_wac.c:1381:4: error: too few arguments to function &#8216;input_mt_init_slots&#8217;
include/linux/input/mt.h:78:5: note: declared here
/var/lib/dkms/wacom/0.13.0/build/wacom_wac.c:1414:4: error: too few arguments to function &#8216;input_mt_init_slots&#8217;
include/linux/input/mt.h:78:5: note: declared here
/var/lib/dkms/wacom/0.13.0/build/wacom_wac.c:1476:5: error: too few arguments to function &#8216;input_mt_init_slots&#8217;
include/linux/input/mt.h:78:5: note: declared here
/var/lib/dkms/wacom/0.13.0/build/wacom_wac.c:1482:5: error: too few arguments to function &#8216;input_mt_init_slots&#8217;
include/linux/input/mt.h:78:5: note: declared here
cc1: some warnings being treated as errors
make[2]: *** [/var/lib/dkms/wacom/0.13.0/build/wacom_wac.o] Error 1
make[1]: *** [_module_/var/lib/dkms/wacom/0.13.0/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-34-generic'
make: *** [all] Error 2[/FONT]

I am only five days old on Ubuntu environment. Any guidance to sort this out will be highly appreciated.

Nilanjan

---

