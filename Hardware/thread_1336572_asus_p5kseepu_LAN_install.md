---
title: "asus p5kse/epu LAN install"
date: 2009-11-24
forum: Hardware
---

### Post by wilsonmorgado on 2009-11-24
Hi. I download linux drivers to install LAN driver off  asus p5kse/epu with  **Atheros(R) L1 Gigabit Ethernet Adapter** . I use Ubuntu 9.10

I change directory to* LinuxDrivers/Lan/src/ *and type **sudo make**, but have a error.


```
sudo make
make -C /lib/modules/2.6.31-15-generic/build SUBDIRS=/home/wilson/Área de Trabalho/l1-linux-v1.2.40.3/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
make[1]: *** No rule to make target `de'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make: *** [default] Error 2
wilson@wilson-desktop:~/Área de Trabalho/l1-linux-v1.2.40.3/src$ 
```

---

