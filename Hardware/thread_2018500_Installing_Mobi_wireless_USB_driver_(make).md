---
title: "Installing Mobi wireless USB driver (make)"
date: 2012-07-06
forum: Hardware
---

### Post by Odaym on 2012-07-06
I have been trying for quite some time today to install the "iBurst compatible driver" from Mobi, it's a driver for an ADSL USB dongle.

I am running Ubuntu 12.04

The instructions say that I have to go into the directory where the driver was unpacked and run **make**. I do so and I get the following:

> 
make -C /lib/modules/3.2.0-26-generic-pae/build SUBDIRS=/home/ali/Mobi Driver modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic-pae'
make[1]: *** No rule to make target `Driver'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic-pae'
make: *** [default] Error 2


I have seen so many threads discussing this "No rule" issue and most of them mention the **build-essential package** and the latest **Linux headers**, both of which **are available** here.

Some of the posts recommended changing the values of some of the variables in the Makefile code (see below) to reflect different paths, others suggest methods that don't apply...and well, I am just lost, I have no idea and this is the only device that can provide me with Internet here at home.

```

MDIR := /lib/modules/$(shell uname -r)
KDIR := $(MDIR)/build
PWD := $(shell pwd)
#EXTRA_CFLAGS :=$(IB_CONFIG_FLAGS)
#export EXTRA_CFLAGS

obj-m = ib-net.o
obj-m += ib-pcmcia.o
obj-m += ib-usb.o
#obj-m += ib-file.o

default:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

install:
	cp *.ko $(MDIR)/kernel/drivers/net/
	echo checking module dependancies...
	depmod -a

uninstall:
	rm $(MDIR)/kernel/drivers/net/ib-*.ko

clean:
	rm -f *.mod.c *.ko *.o .*.cmd core
	rm -fr .tmp_versions
```

Any help is much appreciated, thank you very much in advance!

---

### Post by Odaym on 2012-07-07
bump

---

