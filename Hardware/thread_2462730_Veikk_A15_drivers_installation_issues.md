---
title: "Veikk A15 drivers installation issues"
date: 2021-05-26
forum: Hardware
---

### Post by tgklohn2 on 2021-05-26
I&#8217;m running Ubuntu 20.04.2 LTS, 64-bit, Gnome 3.36.8, and I have the following issues as I tried to install the drivers for the Veikk A15, which is a graphic tablet. I have tried to solve some of the indicated errors individually on my own, but with my little knowledge I couldn&#8217;t go very far:

 tigo2@tigo2:~/Downloads/veikk-linux-driver-master$ make
 make -C /lib/modules/5.8.0-53-generic/build M=/home/tigo2/Downloads/veikk-linux-driver-master modules

 make[1]: Entering directory '/usr/src/linux-headers-5.8.0-53-generic'

 make[1]: Leaving directory '/usr/src/linux-headers-5.8.0-53-generic'
 tigo2@tigo2:~/Downloads/veikk-linux-driver-master$ sudo make install clean
 [sudo] password for tigo2:  
 make -C /lib/modules/5.8.0-53-generic/build M=/home/tigo2/Downloads/veikk-linux-driver-master modules_install

 make[1]: Entering directory '/usr/src/linux-headers-5.8.0-53-generic'

   INSTALL /home/tigo2/Downloads/veikk-linux-driver-master/veikk.ko

 At main.c:160:
 - SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:69
 - SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:76
 sign-file: certs/signing_key.pem: No such file or directory
   DEPMOD  5.8.0-53-generic
 Warning: modules_install: missing 'System.map' file. Skipping depmod.
 make[1]: Leaving directory '/usr/src/linux-headers-5.8.0-53-generic'
 depmod
 modprobe veikk
 mkdir -p /etc/modules-load.d
 echo "veikk" > /etc/modules-load.d/veikk.conf
 make -C /lib/modules/5.8.0-53-generic/build M=/home/tigo2/Downloads/veikk-linux-driver-master clean
 make[1]: Entering directory '/usr/src/linux-headers-5.8.0-53-generic'
   CLEAN   /home/tigo2/Downloads/veikk-linux-driver-master/Module.symvers
 make[1]: Leaving directory '/usr/src/linux-headers-5.8.0-53-generic'
 tigo2@tigo2:~/Downloads/veikk-linux-driver-master$

---

