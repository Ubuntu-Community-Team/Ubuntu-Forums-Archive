---
title: "trying to install cnet network simulator in ubuntu 8.10"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by BujarM on 2009-03-10
Hello, im trying to install cnet network simulator in Ubuntu 8,10

i followed instructions from [http://applegrew.blogspot.com/2007/09/how-to-install-cnet-network-simulator.html](http://applegrew.blogspot.com/2007/09/how-to-install-cnet-network-simulator.html)

but i get this mist&#1072;ke:

bujar@ubuntu:~/abc/cnet-2.0.10$ sudo make install
(cd src && make)
make[1]: Entering directory `/home/bujar/abc/cnet-2.0.10/src'
Linux 2.6.27-7-generic
make[2]: Entering directory `/home/bujar/abc/cnet-2.0.10/src'
make[2]: `cnet' is up to date.
make[2]: Leaving directory `/home/bujar/abc/cnet-2.0.10/src'
cp cnet ../cnet
make[1]: Leaving directory `/home/bujar/abc/cnet-2.0.10/src'
cp cnet /cslinux/bin/cnet
cp: cannot create regular file `/cslinux/bin/cnet': No such file or directory
make: *** [install] Error 1

i have no idea how to fix it 

can someone try to install it by using the same instructions
and tell me if they succeed

thanks in advance
Bujar M

---

