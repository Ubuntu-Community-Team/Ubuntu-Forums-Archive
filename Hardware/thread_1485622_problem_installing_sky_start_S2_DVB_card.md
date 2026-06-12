---
title: "problem installing sky start S2 DVB card"
date: 2010-05-17
forum: Hardware
---

### Post by asemoon on 2010-05-17
Hi,
I have replaced my old skystar2 DVB card with a new skystar **S2** card,I'm running Ubuntu 9.10 and my kernel version is 2.6.31-14-generic
here is the result of dmesg for my dvb card
```
[   14.713166] DVB: registering new adapter (FlexCop Digital TV device)
```

and here is the result for my lspci -vv |grep -i dvb
```
03:07.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
	Subsystem: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card

```

with  that configuration there was no device in my /dev folder so
 I downloaded v4linux driver from linuxTV website and compiled and installed it .after reboot, modules are loaded successfully but still the /dev folder has not an entry for a dvb device(as if it's not installed at all)
then I checked Technisat website for a solution , I came up with the followng tutorial:
```

How to install SkyStar 2 revision 3.3 (DVB-S2 version) using the binary-driver for the CX24120?

0) Have linux-installation which allows to build external kernel modules.

Further help can be found here: http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers

1) Get the complete v4l-dvb driver tree from 2008-09-15 (*) and extract it

 # wget http://linuxtv.org/hg/v4l-dvb/archive/6a9d064fe0ee.tar.bz2
 # tar xfj 6a9d064fe0ee.tar.bz2
 # cd v4l-dvb-6a9d064fe0ee

2) Apply the patch and copy the appropriate driver-binary

 # patch -p1 < <path-to-patch-file>/skystar2-dvb-s2-v4l-dvb.patch
 # cp <path-to-binary-file>/cx24120_blob.o.x86-64 v4l/cx24120_blob.o_shipped # for 64-bit installations
or
 # cp <path-to-binary-file>/cx24120_blob.o.i386   v4l/cx24120_blob.o_shipped # for 32-bit installations

3) (optional) select the device/card-drivers to compile and install

 # make menuconfig

   follow the menus and enable at least

  <M>   Technisat/B2C2 FlexCopII(b) and FlexCopIII adapters
  <M>     Technisat/B2C2 Air/Sky/Cable2PC PCI
  <M>     Technisat/B2C2 Air/Sky/Cable2PC USB

4) Install firmware binary

The CX24120 requires a firmware to operate normally. The file is called "dvb-fe-cx24120-1.20.58.2.fw" and has to be put into the system's firmware directory.

/usr/lib/hotplug/firmware
or
/lib/firmware

for example you can do:
 # cp <path-to-binary-file>/dvb-fe-cx24120-1.20.58.2.fw /usr/lib/hotplug/firmware

5) compile all/selected modules and install them

 # make
 # make install

 the last command will replace the modules which were delivered by the install kernel by the ones you just compiled.

6) Loading the modules. The command 'make install' installed the new driver into the right place and replaced old ones. The next reboot will load these modules automatically. To force a reload of the new modules without rebooting run:

 # make reload

(*) it is important that the version from this day is used, because the binary module "cx24120.ko" requires binary compatibility with the DVB-API provided by the v4l-dvb-tree. If the internal binary API has changed, which can happen without notice, the module will not work. This only applied for types and function provided by the v4l-dvb-tree, i2c and module related things can be found in cx24113_i2c.c and are compiled on this platform.

```
everything is fine until the make stage which I get an error as following
```

/programs/v4l-dvb-6a9d064fe0ee/v4l/au0828-i2c.c:317: error: unknown field 'client_register' specified in initializer
/programs/v4l-dvb-6a9d064fe0ee/v4l/au0828-i2c.c:317: warning: initialization from incompatible pointer type
/programs/v4l-dvb-6a9d064fe0ee/v4l/au0828-i2c.c:318: error: unknown field 'client_unregister' specified in initializer
make[3]: *** [/programs/v4l-dvb-6a9d064fe0ee/v4l/au0828-i2c.o] Error 1

```

what am I doing wrong? do I pick the wrong driver? is this an issue with  kernel version? what should I do to get my card running?

thanks in advance

---

### Post by RobRob89 on 2010-10-24
Hi! I do have exactly the same problem. Did you get it ?

---

