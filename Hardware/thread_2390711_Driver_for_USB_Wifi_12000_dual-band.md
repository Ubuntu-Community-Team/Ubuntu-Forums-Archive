---
title: "Driver for USB Wifi 12000 dual-band"
date: 2018-05-01
forum: Hardware
---

### Post by felipegar on 2018-05-01
Hello:
  I've installed Ubuntu 18.04.
  But unable to install driver for AC 1200 Dual-Band usb 3.0 Adapter.
  When try to compile driver (cd included with wifi adapter) I receive this error:
  
> make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-20-generic/build M=/root/tmp/driver/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333  modules
make[1]: se entra en el directorio '/usr/src/linux-headers-4.15.0-20-generic'
  CC [M]  /root/tmp/driver/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/core/rtw_cmd.o
In file included from /root/tmp/driver/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/include/basic_types.h:80:0,
                 from /root/tmp/driver/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/include/drv_types.h:31,
                 from /root/tmp/driver/rtl88x2BU_WiFi_linux_v5.1.7_19806.20161025_BTCOEX20161024-3333/core/rtw_cmd.c:22:
./include/linux/types.h:17:9: error: unknown type name ‘__kernel_ino_t’
 typedef __kernel_ino_t  ino_t;
         ^~~~~~~~~~~~~~
./include/linux/types.h:18:9: error: unknown type name ‘__kernel_mode_t’
 typedef __kernel_mode_t  mode_t;
         ^~~~~~~~~~~~~~~
./include/linux/types.h:21:9: error: unknown type name ‘__kernel_off_t’
 typedef __kernel_off_t  off_t;
         ^~~~~~~~~~~~~~
./include/linux/types.h:22:9: error: unknown type name ‘__kernel_pid_t’
 typedef __kernel_pid_t  pid_t;
---


Any suggestion?
Thanks

---

