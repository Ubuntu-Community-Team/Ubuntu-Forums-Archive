---
title: "ndiswrapper error"
date: 2004-11-27
forum: Hardware &amp; Laptops
---

### Post by xethm55 on 2004-11-27
I built the ndiswrapper-0.12 with the following output
[I][INDENT]make -C driver install
make[1]: Entering directory `/home/xethm55/ndiswrapper-0.12/driver'
make -C /lib/modules/2.6.8.1-3-k7/build SUBDIRS=/home/xethm55/ndiswrapper-0.12/driver \
        NDISWRAPPER_VERSION=0.12 \
        EXTRA_VERSION= modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.8.1-3-k7'
  CC [M]  /home/xethm55/ndiswrapper-0.12/driver/wrapper.o
  CC [M]  /home/xethm55/ndiswrapper-0.12/driver/iw_ndis.o
  CC [M]  /home/xethm55/ndiswrapper-0.12/driver/pe_loader.o
  CC [M]  /home/xethm55/ndiswrapper-0.12/driver/ndis.o
  CC [M]  /home/xethm55/ndiswrapper-0.12/driver/ntoskernel.o
  CC [M]  /home/xethm55/ndiswrapper-0.12/driver/misc_funcs.o
  CC [M]  /home/xethm55/ndiswrapper-0.12/driver/proc.o
  CC [M]  /home/xethm55/ndiswrapper-0.12/driver/divdi3.o
  CC [M]  /home/xethm55/ndiswrapper-0.12/driver/hal.o
  CC [M]  /home/xethm55/ndiswrapper-0.12/driver/usb.o
  LD [M]  /home/xethm55/ndiswrapper-0.12/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/xethm55/ndiswrapper-0.12/driver/ndiswrapper.mod.o
  LD [M]  /home/xethm55/ndiswrapper-0.12/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.8.1-3-k7'
mkdir -p /lib/modules/2.6.8.1-3-k7/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.8.1-3-k7/misc
/sbin/depmod -a
make[1]: Leaving directory `/home/xethm55/ndiswrapper-0.12/driver'
make -C utils install
make[1]: Entering directory `/home/xethm55/ndiswrapper-0.12/utils'
cc -Wall -g -DNDISWRAPPER_VERSION=\"0.12\"    -c -o loadndisdriver.o loadndisdriver.c
gcc -o loadndisdriver loadndisdriver.o
install -m 755 loadndisdriver /sbin
install -m 755 ndiswrapper /usr/sbin
install -m 755 ndiswrapper-buginfo /usr/sbin
make[1]: Leaving directory `/home/xethm55/ndiswrapper-0.12/utils'[/INDENT]
[/I]
I then entered the following command:
*[CENTER]ndiswrapper -i file.inf[/CENTER] *
when i try to run the command
                   [CENTER]  * modprobe ndiswrapper*[/CENTER]
i get the following error:
[CENTER]*FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-3-k7/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid module format*[/CENTER]

what does it mean, and how do i fix it.  
thank you

---

### Post by mr_ed on 2004-11-29
I got that very same error when I first ran ndiswrapper.  I ran it without inserting a module, so it obviously couldn't find the driver.

BTW, for future reference, instead of downloading and building it from their site, just go into Synaptic and downlaod the ndiswrapper-utils package.  (I think that's what it's called... do a search for ndiswrapper and you'll find it)

Make sure that you got your case matches the inf file when running ndiswrapper -i file.inf.

In my case it was
ndiswrapper -i NET8180.INF
and I typed
ndiswrapper -i net8180.inf

so I had to delete the /etc/ndiswrapper folder and try again with it all uppercase.

---

### Post by jdodson on 2004-11-30
ya gnu/linux is case sensitive.  however in my case i had to roll ndiswrapper from source because my wireless is my internet connection.  not a big deal, in the end had to apt-get gcc and kernel-headers from the cd.  worked fine.

---

