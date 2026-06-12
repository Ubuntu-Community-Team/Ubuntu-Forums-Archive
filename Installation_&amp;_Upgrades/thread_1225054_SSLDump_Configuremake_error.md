---
title: "SSLDump Configure/make error"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by s92o on 2009-07-28
Hi, im a (almost complete) linux noob, so bare with me. i have recently tried to install SSLDump-0.9b3, and there has been an error in the configure file, this is what i got:  sudo ./configure
loading cache ./config.cache
checking host system type... rm: cannot remove `dummy': Is a directory
rm: cannot remove `dummy': Is a directory
configure: error: can not guess host type; you must specify one, now im guessing that i would need to specify a host type, but i just decided to move dummy, (that dir) just to see what would happen. It ended up configuring smoothly. now when i sudo make, this happens: gcc -g -O2  -DHAVE_LIBM=1 -DHAVE_SYS_TIME_H=1 -DSTDC_HEADERS=1 -DTIME_WITH_SYS_TIME=1 -DSIZEOF_UNSIGNED_SHORT=2 -DSIZEOF_UNSIGNED_INT=4 -DSIZEOF_UNSIGNED_LONG=8 -DSIZEOF_UNSIGNED_LONG_LONG=8-DRETSIGTYPE=void -DHAVE_VPRINTF=1 -DHAVE_STRDUP=1   -c -o network.o ./base/network.c         -DOPENSSL    -I./base/   -I./null/   -I./ssl/   -Icommon/include/ -I./null/ -I./ssl/ -I/usr/include -I/usr/local/include
In file included from ./base/network.h:96,
                 from ./base/network.c:51:
./base/tcpconn.h:53: error: expected specifier-qualifier-list before ‘tcp_seq’
./base/tcpconn.h:59: error: expected specifier-qualifier-list before ‘tcp_seq’
make: *** [network.o] Error 1, now im not really understanding whats going on here. ive been googling and surprisingly have only found like 3 topics that have the word ssldump in it. (From what i see, no1 EVER has problems with ssldump) so if you could help me it would be much appreciated.

---

### Post by Partyboi2 on 2009-07-28
Hi, an easier way of installing it is to install the one in the Ubuntu repos. You can either open up Synaptic Package Manager (System>Admin>Synaptic Package Manager) and search for 'ssldump' and install. Or open a terminal (Applications>Accessories>Terminal) and install with
```
sudo apt-get install ssldump
```

---

