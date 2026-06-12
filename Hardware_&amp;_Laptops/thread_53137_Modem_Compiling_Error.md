---
title: "Modem Compiling Error"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by rebalde on 2005-07-30
Part way through the compiling process, using "make" , I get this error:

make modules: -C /lib/modules/2.6.10-5-386/build
make: *** /lib/modules/2.6.10-5-386/build:  No subh file or directory. Stop

at this piont the "make" program aborts.

can someone tell me if I'm missing a package and if so, which one, or is there something else wrong.

the linux driver I'm trying to compile is slmodem-2.9.7 ..  I got it off the install cd that came with my SupraMax modem.

thanks a bunch

rebel

---

### Post by pestilence4hr on 2005-07-30
[QUOTE=rebalde]
make modules: -C /lib/modules/2.6.10-5-386/build
make: *** /lib/modules/2.6.10-5-386/build:  No subh file or directory. Stop
[/QUOTE]


```
sudo apt-get install linux-headers-`uname -r`
```

---

