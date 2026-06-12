---
title: "pb installing (building) xmail"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by mbarka on 2009-02-10
hello
while trying building xmail
make -f Makefile.lnx
i had this error
g++ -o bin/MkMachDep MkMachDep.o -lssl -lcrypto -ldl -lpthread
/usr/bin/ld: cannot find -lssl
collect2: ld a retourné 1 code d'état d'exécution
make: *** [bin/MkMachDep] Erreur
what are the packages i should install.
i'am a biguinner in ubuntu. (i use ubuntu server 8.04)
thanks

---

### Post by mbarka on 2009-02-10
sudo apt-get install openssl*

---

