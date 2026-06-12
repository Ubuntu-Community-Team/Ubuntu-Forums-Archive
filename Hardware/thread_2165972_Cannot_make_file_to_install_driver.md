---
title: "Cannot make file to install driver"
date: 2013-08-07
forum: Hardware
---

### Post by daniel-crosby9 on 2013-08-07
Hi all

Im currently trying to install drivers for my wireless card. When i use the terminal and navigate to the directory and enter the command *make* i get this error.

> make -C /lib/modules/3.5.0-37-generic/build M=/home/daniel/wireless/wlan/rtl8723e modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-37-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "rtl_query_rxpwrpercentage" [/home/daniel/wireless/wlan/rtl8723e/rtl8723e.ko] undefined!
WARNING: "rtl_evm_db_to_percentage" [/home/daniel/wireless/wlan/rtl8723e/rtl8723e.ko] undefined!
WARNING: "rtl_signal_scale_mapping" [/home/daniel/wireless/wlan/rtl8723e/rtl8723e.ko] undefined!
WARNING: "rtl_process_phyinfo" [/home/daniel/wireless/wlan/rtl8723e/rtl8723e.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-37-generic'

Can anyone advise what to do to get this working so i can use my wireless.

---

### Post by ian-weisser on 2013-08-07
Oops. 
My mistaken advice retracted....

---

### Post by Yellow Pasque on 2013-08-07
> **ian-weisser said:**
> Installing modules is a root (not user) activity. You should be using "sudo make"

No, the user is in a sub-directory of his home, so 'make' is preferred. 'sudo' is only needed for 'make install'.

---

