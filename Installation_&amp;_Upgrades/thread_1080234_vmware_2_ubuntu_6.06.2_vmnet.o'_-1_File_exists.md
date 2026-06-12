---
title: "vmware 2 ubuntu 6.06.2 vmnet.o': -1 File exists"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by duxbuz on 2009-02-25
I am trying to install vmware 2 onto ubuntu 6.06.2

it compiles most of it but then last bit i get

make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-53-server'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config1/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config1/vmnet.o': -1 File exists
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

Anyone know if there is a simple fix, or do i have to recompile kernel, which i know i wont do, as its proxy server and i need it up and running.

I will have to build another machine with it on, if i cant get it to work

Ta

---

