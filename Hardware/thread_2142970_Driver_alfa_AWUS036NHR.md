---
title: "Driver alfa AWUS036NHR"
date: 2013-05-07
forum: Hardware
---

### Post by jackdispade on 2013-05-07
Hello,   
I have a problem with Alpha AWUS063NHR network card drivers and i'm not able to install. 

This is the error message:       

```
Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.2.6/build M=/root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715  modules
make[1]: Entering directory `/usr/src/linux-source-3.2.6'

  WARNING: Symbol version dump /usr/src/linux-source-3.2.6/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o
In file included from /root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.c:24:
/root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h:49:29: error: linux/smp_lock.h: No such file or directory
In file included from /root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/include/drv_types.h:69,
                 from /root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.c:25:
/root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_recv.h: In function ‘rxmem_to_recvframe’:
/root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_recv.h:622: warning: cast from pointer to integer of different size
/root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/include/rtw_recv.h:622: warning: cast to pointer from integer of different size
make[2]: *** [/root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715] Error 2
make[1]: Leaving directory `/usr/src/linux-source-3.2.6'
make: *** [modules] Error 2
Compile make driver error: 2, Please check error Mesg


```

The OS is: Backtract 5 RC3  
I have tried everything but i have the same problem. Somebody can help me?

---

