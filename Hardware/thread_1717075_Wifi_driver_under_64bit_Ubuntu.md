---
title: "Wifi driver under 64bit Ubuntu"
date: 2011-03-29
forum: Hardware
---

### Post by randomAccess on 2011-03-29
I've bought a wifi usb dongle which uses Realtek RTL8192CU driver. I've downloaded the driver from Realtek's site and got into troubles during the make process. Here are the steps

   1. Extract the file and go into this new folder
   2. sudo sh ./install
   3. After the message "The Setup Script is completed !Plese Press any keyword to exit.", I went into /drivers into directory rtl8192CU_linux_v2.0.1324.20110126
   4. sudo make

    > make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/2.6.35-28-generic/build M=/home/xxx/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v2.0.1324.20110126/driver/rtl8192CU_linux_v2.0.1324.20110126 modules make[1]: Entering directory /usr/src/linux-headers-2.6.35-28-generic' Building modules, stage 2. MODPOST 1 modules make[1]: Leaving directory /usr/src/linux-headers-2.6.35-28-generic'

   5. sudo ./clean

    ```
ERROR: Module r8192s_usb does not exist in /proc/modules
    ERROR: Module ieee80211_rsl does not exist in /proc/modules
    ERROR: Module ieee80211_crypt_ccmp does not exist in /proc/modules
    ERROR: Module ieee80211_crypt_tkip does not exist in /proc/modules
    ERROR: Module ieee80211_crypt_wep does not exist in /proc/modules
    ERROR: Module ieee80211_crypt does not exist in /proc/modules
```

   6. sudo insmod 8192cu.ko

    ```
insmod: error inserting '8192cu.ko': -1 File exists
```

So basically, I cannot insert compiled module. Please help.

PS. I use Ubuntu 10.10 x64

---

### Post by Yellow Pasque on 2011-03-29
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)
More specifically, [http://linuxwireless.org/en/users/Drivers/rtl819x](http://linuxwireless.org/en/users/Drivers/rtl819x)

---

### Post by randomAccess on 2011-03-29
THANKS A LOT! For days I've been trying all kinds of original drivers and I wasn't able to make Ubuntu even see the dongle. Now I complied this driver, rebooted and voila - it works :D

---

