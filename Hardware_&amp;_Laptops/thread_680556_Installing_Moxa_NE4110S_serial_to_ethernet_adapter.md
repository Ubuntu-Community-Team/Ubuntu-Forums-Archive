---
title: "Installing Moxa NE4110S serial to ethernet adapter"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by emprise on 2008-01-28
[SIZE="2"]hello i am new to ubuntu as well as linux. i am trying to install the drivers for the NE4110S serial to ethernet adapter from moxa. the user guide says download the .tgz package and extract it in root folder and Execute /tmp/moxa/mxinst.
i have downloaded the package but i am unable to copy it to the root folder permission denied error occurs. what shall i do to install it.i am yet to receive any details from the moxa support team . any takers will be greatly appriciated.

gutsy gibbon is my ubuntu.
:confused:

thanks in advance.[/SIZE]

---

### Post by emprise on 2008-01-29
hi 
here is the code which i get when i try to execute the commands given in ne4100 series manual.
hope somebody might help me to sort this out.:confused:

********************************************************
adminemp@desktop:/$ cd tmp
adminemp@desktop:/tmp$ cd..
bash: cd..: command not found
adminemp@desktop:/tmp$ cd /
adminemp@desktop:/$ /tmp/moxa/mxinst

===============================================================================
Copyright (C) 2002-2007  Moxa Technologies Co., Ltd.
All Rights Reserved.

MOXA NPort Server Real TTY Driver V1.14 Installation.
System Imformation: Kernel 2.6.22-14-generic; Machine i686.
===============================================================================

touch: cannot touch `/etc/init.d/npreals': Permission denied

Tar files, please wait ... OK!
Building driver...

If you want to use secure communication with target,
you might choose [y] to enable the SSL function.
Note: This function support RealCOM with secure mode only.
Do you want to enable secure function? [y/N].
n
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/tmp/moxa modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/moxa/npreal2.o
/tmp/moxa/npreal2.c: In function ‘npreal_open’:
/tmp/moxa/npreal2.c:970: warning: assignment makes integer from pointer without a cast
/tmp/moxa/npreal2.c: In function ‘npreal_block_til_ready’:
/tmp/moxa/npreal2.c:1728: warning: comparison between pointer and integer
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/moxa/npreal2.mod.o
  LD [M]  /tmp/moxa/npreal2.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
cp -p npreal2.ko /lib/modules/2.6.22-14-generic/kernel/drivers/char/
cp: cannot create regular file `/lib/modules/2.6.22-14-generic/kernel/drivers/char/npreal2.ko': Permission denied
make: *** [module] Error 1
Check Driver...
FAILED !!!
 
Install Not Completed !
****************************************

---

