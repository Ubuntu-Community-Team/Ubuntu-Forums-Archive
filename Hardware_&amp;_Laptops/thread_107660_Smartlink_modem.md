---
title: "Smartlink modem?"
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by MaaSTaaR on 2005-12-23
Hello ...

i have Tohiba Satellite A10 laptop , and it's modem is Smartlink (it's name in Windows Toshiba Software Modem AMR) , i downloaded modem drives and try to install it , but when i do "make" command it's show for me these errors :


```
root@MaaSTaaR:/home/maastaar/Desktop/mdm# make
make -C modem all
make[1]: Entering directory `/home/maastaar/Desktop/mdm/modem'
rebuild profile...
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_main.o -c modem_main.c
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem_cmdline.o -c modem_cmdline.cgcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem.o -c modem.c
modem.c: In function â€&#1705;modem_resetâ€™:
modem.c:1701: error: invalid storage class for function â€&#1705;sregs_initâ€™
modem.c:1713: warning: implicit declaration of function â€&#1705;sregs_initâ€™
modem.c: At top level:
modem.c:1727: error: static declaration of â€&#1705;sregs_initâ€™ follows non-static declaration
modem.c:1713: error: previous implicit declaration of â€&#1705;sregs_initâ€™ was here
make[1]: *** [modem.o] Error 1
make[1]: Leaving directory `/home/maastaar/Desktop/mdm/modem'
make: *** [modem] Error 2

```

and when i do "make install"

```
root@MaaSTaaR:/home/maastaar/Desktop/mdm# make install
make -C modem all
make[1]: Entering directory `/home/maastaar/Desktop/mdm/modem'
gcc -Wall -g -O -I. -DCONFIG_DEBUG_MODEM   -o modem.o -c modem.c
modem.c: In function â€&#1705;modem_resetâ€™:
modem.c:1701: error: invalid storage class for function â€&#1705;sregs_initâ€™
modem.c:1713: warning: implicit declaration of function â€&#1705;sregs_initâ€™
modem.c: At top level:
modem.c:1727: error: static declaration of â€&#1705;sregs_initâ€™ follows non-static declaration
modem.c:1713: error: previous implicit declaration of â€&#1705;sregs_initâ€™ was here
make[1]: *** [modem.o] Error 1
make[1]: Leaving directory `/home/maastaar/Desktop/mdm/modem'
make: *** [modem] Error 2
```

what should i do to install this drive and connect to the internet with ubuntu ?

---

### Post by towsonu2003 on 2005-12-24
check out [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) especially where it talks about smartlink (see right side 'contents'), it should be helpful.

---

