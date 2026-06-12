---
title: "Ethernet driver woes..still cannot install after readingd every related post."
date: 2012-11-13
forum: Hardware
---

### Post by viyat001 on 2012-11-13
THis is error message I got when trying to compile compat-wireless 3.5.1-1-snpc.tar.bz2

viyat@viyat-Lenovo-G580:~/compat-wireless-3.5.1-1-snpc$ ./scripts/driver-select alx
bash: ./scripts/driver-select: Permission denied
viyat@viyat-Lenovo-G580:~/compat-wireless-3.5.1-1-snpc$ make
/bin/sh: 1: ./compat/scripts/gen-compat-config.sh: Permission denied
make: *** [/home/viyat/compat-wireless-3.5.1-1-snpc/.compat_autoconf_compat-wireless-v3.5.1-1-snpc] Error 126
viyat@viyat-Lenovo-G580:~/compat-wireless-3.5.1-1-snpc$ sudo make install
[sudo] password for viyat: 
make: execvp: ./scripts/update-initramfs: Permission denied
make: *** [uninstall] Error 127
viyat@viyat-Lenovo-G580:~/compat-wireless-3.5.1-1-snpc$ 

Please help! Thank you.

---

### Post by gerowen on 2012-11-14
It appears as if you may not have the permissions necessary to execute the files you have downloaded.  Try doing:

```
sudo chmod -R a+rx /DRIVERS/FOLDER
```

Where /DRIVERS/FOLDER is the folder where you've extracted the drivers for your card, then try compiling it again.

---

### Post by viyat001 on 2012-11-15
Thank you very much. That helped. Ethernet working!!

---

