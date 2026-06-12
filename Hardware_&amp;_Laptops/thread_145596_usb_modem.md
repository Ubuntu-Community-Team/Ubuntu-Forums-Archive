---
title: "usb modem"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by chris23 on 2006-03-16
hello,i have a smart usb 56k modem and ubuntu 5.10, I 've downloaded the drivers...i followed the instructions included and when i try to run the make command the following error occured...
any help?

make[1]: Entering directory `/home/christos/slmodem/modem'
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM -o modem.o -c modem.c
modem.c: In function ‘modem_reset’:
modem.c:1701: error: invalid storage class for function ‘sregs_init’
modem.c:1713: warning: implicit declaration of function ‘sregs_init’
modem.c: At top level:
modem.c:1727: error: static declaration of ‘sregs_init’ follows non-static declaration
modem.c:1713: error: previous implicit declaration of ‘sregs_init’ was here
make[1]: *** [modem.o] Error 1
make[1]: Leaving directory `/home/christos/slmodem/modem'
make: *** [modem] Error 2

---

### Post by chris23 on 2006-03-17
any help guys?

---

