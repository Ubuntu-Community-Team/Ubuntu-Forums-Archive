---
title: "rtl8187 and kernel 2.6.31+ ubuntu 9.10"
date: 2009-08-26
forum: Hardware
---

### Post by BuMRK on 2009-08-26
Helo,

I have a problem with the compilation rtl8187L drivers from the kernel 2.6.31+ there is such an error

Code: /home/bum/tmp/rtl8187L_linux_26.1037.1217.2008_release/ieee80211/ieee80211_module.c:121: error: 'struct net_device' has no member named 'hard_start_xmit'

---

### Post by Nano.uy on 2009-11-01
I have the same trouble when I try to compile drivers for RTL8187B: 

```
nano@nano-laptop:~/Respaldos/Drivers/rtl8187b$ makemake[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.31-14-generic'
CC [M] /home/nano/Respaldos/Drivers/rtl8187b/ieee80211/ieee80211_module.o
/home/nano/Respaldos/Drivers/rtl8187b/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rtl’:
/home/nano/Respaldos/Drivers/rtl8187b/ieee80211/ieee80211_module.c:121: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/nano/Respaldos/Drivers/rtl8187b/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/nano/Respaldos/Drivers/rtl8187b/ieee80211] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2
nano@nano-laptop:~/Respaldos/Drivers/rtl8187b$ 

```

Looking in google I found that: 

"[...] linux kernel 2.6.31. This kernel removes backwards compatibility for the old network driver api. Only the new net_driver_ops structure api is supported. "

I think that it means that in kernel 2.6.31 the structure of this kind of drivers is not supported, but I don't know how to fix.

---

### Post by Roman10 on 2009-11-24
Me too... ](*,)](*,)](*,)](*,)

---

### Post by go_beep_yourself on 2009-11-30
I got it to compile. Get the latest rtl8187 source code at [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

---

### Post by luks911 on 2009-12-09
> **go_beep_yourself said:**
> I got it to compile. Get the latest rtl8187 source code at [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

How did you do it? I compiled the compat-wireless driver without problems, but I have the same error when I try to compile the rtl8187L driver.
Thanks

---

