---
title: "FANS problems with ASPIRE5738ZG"
date: 2010-10-01
forum: Hardware
---

### Post by marcisim on 2010-10-01
Hi every body!

I've got an Acer Aspire 5738ZG. I use UBUNTU, but since I installed it, I've got problems with the fans. I found out that it is a common problem for acers with ubuntu and it may be solved as illustrated here:

[https://help.ubuntu.com/community/Aspire1810TZ/Karmic](https://help.ubuntu.com/community/Aspire1810TZ/Karmic)

Though, after downloading and unpackaging, I found this problem:

[COLOR=Silver]marcisim@tnagia[/COLOR]$[B]make
make -C /lib/modules/2.6.32-23-generic/build  SUBDIRS=/home/marcisim/Downloads/acerhdf_kmod modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
  CC [M]  /home/marcisim/Downloads/acerhdf_kmod/acerhdf.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/marcisim/Downloads/acerhdf_kmod/acerhdf.mod.o
  LD [M]  /home/marcisim/Downloads/acerhdf_kmod/acerhdf.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'[/B]
[COLOR=Silver]
[/COLOR][B][COLOR=Silver]marcisim@tnagia$[/COLOR]sudo make install
make -C /lib/modules/2.6.32-23-generic/build  SUBDIRS=/home/marcisim/Downloads/acerhdf_kmod modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
[ -d /lib/modules/2.6.32-23-generic/updates ] || mkdir /lib/modules/2.6.32-23-generic/updates
cp acerhdf.ko /lib/modules/2.6.32-23-generic/updates/
depmod -a[/B]
[COLOR=Silver]
[/COLOR][B][COLOR=Silver]marcisim@tnagia$[/COLOR]sudo modprobe acerhdf
[COLOR=Red]WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Error inserting acerhdf (/lib/modules/2.6.32-23-generic/updates/acerhdf.ko): No such device[/COLOR][/B][COLOR=Red]
[/COLOR]
can anybody help me?

---

### Post by marcisim on 2010-10-01
bump

---

### Post by marcisim on 2010-10-01
bump

---

### Post by marcisim on 2010-10-01
I noticed that this problem affected kernels before linux - 2.6.31-11.38.
I actually have 2.6.32-23, anyway..

anybody?

---

### Post by marcisim on 2011-04-23
bump

---

