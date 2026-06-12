---
title: "compal-laptop module fully inside the kernel?"
date: 2009-05-07
forum: Hardware
---

### Post by kforum on 2009-05-07
as of jaunty, it seems to be there for sure, however the 'battery charge level' function clearly isnt, which is odd...
all of the other sys items are there.

the full compal-laptop modules should also create the:
cat /sys/devices/platform/compal-laptop/charging_level
entries, and it hasnt.

anyone with more knowlegde or better understanding of this would care to shed a light?

also, as of kernel .27 the compal-laptop module was added to the main linux kernel.


cheers

---

### Post by kforum on 2009-05-08
no one knows as usual...

---

### Post by loomsen on 2009-06-02
Hi.

[http://eko.one.pl/index.php?page=compal-laptop](http://eko.one.pl/index.php?page=compal-laptop)

Get the driver. The implementation into the kernel means you will be able to access this module if you have an appropriate driver...

```

[root@tiffy compal-laptop-0.2.9-2.6.29]# pwd
       /opt/compal-laptop-0.2.9-2.6.29
[root@tiffy compal-laptop-0.2.9-2.6.29]# cd ..
[root@tiffy opt]# mv compal-laptop-0.2.9-2.6.29/ /usr/src/
[root@tiffy opt]# cd /usr/src/
[root@tiffy src]# ls
       akmods  compal-laptop-0.2.9-2.6.29  kernels
[root@tiffy src]# cd compal-laptop-0.2.9-2.6.29/
[root@tiffy compal-laptop-0.2.9-2.6.29]# ls
       compal-laptop-0.2.9-2.6.29.patch  compal-laptop.c  Makefile
[root@tiffy compal-laptop-0.2.9-2.6.29]# make && make install
       Building Compal Laptop Extras...
       make[1]: Entering directory `/usr/src/kernels/2.6.29.4-167.fc11.x86_64'
         CC [M]  /usr/src/compal-laptop-0.2.9-2.6.29/compal-laptop.o
         Building modules, stage 2.
         MODPOST 1 modules
         CC      /usr/src/compal-laptop-0.2.9-2.6.29/compal-laptop.mod.o
         LD [M]  /usr/src/compal-laptop-0.2.9-2.6.29/compal-laptop.ko
       make[1]: Leaving directory `/usr/src/kernels/2.6.29.4-167.fc11.x86_64'
       Installing Compal Laptop Extras...
       mkdir -p /lib/modules/`uname -r`/kernel/drivers/platform/x86
       rm /lib/modules/`uname -r`/kernel/drivers/platform/x86/compal-laptop.ko
       cp compal-laptop.ko /lib/modules/`uname -r`/kernel/drivers/platform/x86/
       depmod -ae
[root@tiffy compal-laptop-0.2.9-2.6.29]# insmod ./compal-laptop.ko 
[root@tiffy compal-laptop-0.2.9-2.6.29]# grep compal /proc/modules 
       compal_laptop 5496 0 - Live 0xffffffffa0907000
[root@tiffy compal-laptop-0.2.9-2.6.29]# cd /sys/devices/platform/
[root@tiffy platform]# ls
       compal-laptop     i8042     pcspkr  regulatory.0  uevent
       Fixed MDIO bus.0  iTCO_wdt  power   serial8250    vesafb.0
[root@tiffy platform]# cd compal-laptop/
[root@tiffy compal-laptop]# ls
       bluetooth  charging_level  driver  modalias  power  subsystem  uevent  wlan
[root@tiffy compal-laptop]# cat charging_level 
       80
[root@tiffy compal-laptop]# 

```

---

### Post by kforum on 2009-06-09
thanks, i got this by default:
bluetooth  driver  modalias  power  raw  subsystem  uevent  wlan

but im goign to try the modules compal-laptop supplies(with your instructions).
cheers and many many thanks!

---

