---
title: "problem installing nic"
date: 2008-07-21
forum: Hardware
---

### Post by f_kafka_il on 2008-07-21
i have an onboard nic, Attansic Technology Corp. L2 100 Mbit Ethernet Adapter, the reason im trying to install it is because i get extremly slow speeds with my samba server, sending from linux to windows on 120kbps, some guys gave me a tip to try and install the vendor's linux drivers.

at first i got an error on the makefile: scripts/Makefile.build:46: *** CFLAGS was changed in "/home/kafka/l2-linux-v1.0.40.4/src/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.

but i fixed it by commenting EXTRA_FLAGS on /usr/src/linux-headers-2.6.24-19/scripts/Makefile.build
.

now i got a new error:
/home/kafka/l2-linux-v1.0.40.4/src/at_osdep.h:68:5: warning: "DBG" is not defined
In file included from /home/kafka/l2-linux-v1.0.40.4/src/at_main.c:28:
/home/kafka/l2-linux-v1.0.40.4/src/at.h:46:5: warning: "DBG" is not defined
/home/kafka/l2-linux-v1.0.40.4/src/at_main.c: In function &#1490;at_probe&#1490;:
/home/kafka/l2-linux-v1.0.40.4/src/at_main.c:348: error: implicit declaration of function &#1490;SET_MODULE_OWNER&#1490;
/home/kafka/l2-linux-v1.0.40.4/src/at_main.c: In function &#1490;at_intr_rx&#1490;:
/home/kafka/l2-linux-v1.0.40.4/src/at_main.c:2081: error: implicit declaration of function &#1490;eth_copy_and_sum&#1490;
make[2]: *** [/home/kafka/l2-linux-v1.0.40.4/src/at_main.o] Error 1
make[1]: *** [_module_/home/kafka/l2-linux-v1.0.40.4/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-server'
make: *** [default] Error 2

---

