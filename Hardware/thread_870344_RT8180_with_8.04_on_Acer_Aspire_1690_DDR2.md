---
title: "RT8180 with 8.04 on Acer Aspire 1690 DDR2"
date: 2008-07-25
forum: Hardware
---

### Post by maxinquaye on 2008-07-25
Hello all!

I was trying to compile the drivers for the rt8180 chipset as seen on here:

[http://aircrack-ng.org/doku.php?id=r8180-sa2400]("http://aircrack-ng.org/doku.php?id=r8180-sa2400")

but upon doing the

```
make && make install
```

I get the following error message:
```

gil@gil-laptop:~/rtl8180-0.21$ make && make install
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/gil/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/gil/rtl8180-0.21/ieee80211_rx.o
In file included from /home/gil/rtl8180-0.21/ieee80211_rx.c:43:
/home/gil/rtl8180-0.21/ieee80211.h:43:1: warning: "BIT" redefined
In file included from include/linux/kernel.h:15,
                 from include/linux/skbuff.h:17,
                 from include/linux/if_ether.h:113,
                 from include/linux/netdevice.h:29,
                 from include/linux/if_arp.h:26,
                 from /home/gil/rtl8180-0.21/ieee80211_rx.c:25:
include/linux/bitops.h:6:1: warning: this is the location of the previous definition
/home/gil/rtl8180-0.21/ieee80211_rx.c: In function ‘ieee80211_monitor_rx’:
/home/gil/rtl8180-0.21/ieee80211_rx.c:296: error: ‘struct sk_buff’ has no member named ‘mac’
/home/gil/rtl8180-0.21/ieee80211_rx.c: In function ‘ieee80211_r8180_rx’:
/home/gil/rtl8180-0.21/ieee80211_rx.c:1131: error: ‘struct sk_buff’ has no member named ‘mac’
/home/gil/rtl8180-0.21/ieee80211_rx.c:1131: error: ‘struct sk_buff’ has no member named ‘nh’
/home/gil/rtl8180-0.21/ieee80211_rx.c: At top level:
/home/gil/rtl8180-0.21/ieee80211_rx.c:1163: fatal error: opening dependency file /home/gil/rtl8180-0.21/.ieee80211_rx.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/gil/rtl8180-0.21/ieee80211_rx.o] Error 1
make[1]: *** [_module_/home/gil/rtl8180-0.21] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [2.6] Error 2
```

I am trying this on an ACER Aspire 1690 DDR2 laptop running Hardy Heron. Can anyone help me?

Thanks in advance!

---

