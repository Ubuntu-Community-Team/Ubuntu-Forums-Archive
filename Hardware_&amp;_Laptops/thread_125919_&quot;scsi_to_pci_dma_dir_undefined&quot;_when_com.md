---
title: "&quot;scsi_to_pci_dma_dir undefined&quot; when compiling Highpoint driver"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by The Belgain on 2006-02-05
I'm trying to compile the driver for the Highpoint Rocket 1540 SATA controller, but am hitting a problem with an undefined reference.  It looks like I'm not the first person to have run into [this problem]("http://www.ubuntuforums.org/showthread.php?t=72258").

I've followed [this guide]("http://www.ubuntuforums.org/showthread.php?t=85064") and recompiled the kernel, so I don't think there's any issue with my kernel source setup.

When building the Highpoint driver, I get the following:

```
james@ubuntu-fileserver:~/r1540-openbuild-v1.0$ sudo make KERNELDIR=/usr/src/linux
cp -f hptprot.o hptprot.obj
make -C /usr/src/linux SUBDIRS=`pwd` modules
make[1]: Entering directory `/home/james/linux/linux-source-2.6.12'
  LD [M]  /home/james/r1540-openbuild-v1.0/hptr1540.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/james/r1540-openbuild-v1.0/.hptprot.obj.cmd for /home/james/r1540-openbuild-v1.0/hptprot.obj
*** Warning: "scsi_to_pci_dma_dir" [/home/james/r1540-openbuild-v1.0/hptr1540.ko] undefined!
  LD [M]  /home/james/r1540-openbuild-v1.0/hptr1540.ko
make[1]: Leaving directory `/home/james/linux/linux-source-2.6.12'

```

When I try to insert the module, it complains about unresolved symbols:

```
james@ubuntu-fileserver:~/r1540-openbuild-v1.0$ sudo insmod ./hptr1540.ko
Password:
insmod: error inserting './hptr1540.ko': -1 Unknown symbol in module

```

Has anyone got any ideas?  Do I need to be compiling an extra module into the kernel to solve this?  Help would be very much appreciated, thanks...

---

