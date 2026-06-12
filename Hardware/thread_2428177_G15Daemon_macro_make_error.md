---
title: "G15Daemon macro make error"
date: 2019-09-30
forum: Hardware
---

### Post by kanayel on 2019-09-30
Hi, everyone!

I am trying to install g15daemon to use Logitech G110 Keyboards in my ubuntu 19.04.

But I am getting this error when executing make in macro folder:

```
make  all-am
make[1]: Entering directory '/home/ismael/Downloads/Linux-G15-Daemon-Logitech-G110--master/g15macro-1.0.3'
/bin/bash ./libtool --tag=CC   --mode=link gcc -O3 -Wall -g -O2 -I. -I.  -g -O2 -avoid-version  -o g15macro g15macro.o  -lg15daemon_client -lg15render -lX11 -lXtst 
mkdir .libs
gcc -O3 -Wall -g -O2 -I. -I. -g -O2 -o g15macro g15macro.o  -lg15daemon_client -lg15render -lX11 -lXtst  
/usr/bin/ld: g15macro.o: undefined reference to symbol 'pthread_join@@GLIBC_2.2.5'ndefined reference to symbol 'pthread_join@@GLIBC_2.2.5'
/usr/bin/ld: /lib/x86_64-linux-gnu/libpthread.so.0: error adding symbols: DSO missing from command line
collect2: error: ld returned 1 exit status
make[1]: *** [Makefile:299: g15macro] Error 1
make[1]: Leaving directory '/home/ismael/Downloads/Linux-G15-Daemon-Logitech-G110--master/g15macro-1.0.3'
make: *** [Makefile:215: all] Error 2

```

There are several post with this problem "ndefined reference to symbol 'pthread_join@@GLIBC_2.2.5'" but none of them are related to g15daemon.

Could you help me with that, please?

Ty in advance :)

---

