---
title: "ZTE linux phone driver wont install"
date: 2013-03-28
forum: Hardware
---

### Post by EpicMinerBackup on 2013-03-28
Im getting this ```
sb_driver$ sudo ./install[sudo] password for jeff: 
*** Check for root ***
./install: 5: [: -ne: unexpected operator
ZTE handset driver install...
driver install
this is linux driver installtion
this is customized kernel ,kernel version is: 3.5.0-26-generic
make -C /lib/modules/3.5.0-26-generic/build M=/tmp/ZTE_driver_install modules
make: *** /lib/modules/3.5.0-26-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2
enter customize_driver_install function
cp: cannot stat `zte.ko': No such file or directory
FATAL: Module zte not found.
././driver/ZTE_driver_installV2.11.run: line 13: cd: /home/jeff/Desktop/Untitled: No such file or directory
**********************************************
ZTE handset driver install failed
**********************************************



```

---

### Post by EpicMinerBackup on 2013-03-29
any one o-o

---

### Post by swoonny on 2013-04-02
sudo apt-get install linux-headers-3.5.0-26-generic

---

