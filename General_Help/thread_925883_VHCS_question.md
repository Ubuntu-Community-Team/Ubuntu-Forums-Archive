---
title: "VHCS question"
date: 2008-09-21
forum: General Help
---

### Post by Cool Surfer on 2008-09-21
Hi 
I am trying o install VHCS, but when I run make install command, i get this error.

```
dfx@dfx-desktop:~/Desktop/ubuntu-server/vhcs2-2.4.7.1$ make install
cd ./tools && make install
make[1]: Entering directory `/home/dfx/Desktop/ubuntu-server/vhcs2-2.4.7.1/tools'
cd ./build && make install 
make[2]: Entering directory `/home/dfx/Desktop/ubuntu-server/vhcs2-2.4.7.1/tools/build'
/usr/bin/install -m 0700 -o root -g root ./vhcs2-mkdirs.pl /usr/sbin
/usr/bin/install: cannot remove `/usr/sbin/vhcs2-mkdirs.pl': Permission denied
make[2]: *** [install] Error 1
make[2]: Leaving directory `/home/dfx/Desktop/ubuntu-server/vhcs2-2.4.7.1/tools/build'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/dfx/Desktop/ubuntu-server/vhcs2-2.4.7.1/tools'
make: *** [install] Error 2
dfx@dfx-desktop:~/Desktop/ubuntu-server/vhcs2-2.4.7.1$ 

```

how do I fix this pl.

---

