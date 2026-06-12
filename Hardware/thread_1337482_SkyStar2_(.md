---
title: "SkyStar2 :("
date: 2009-11-25
forum: Hardware
---

### Post by r00te on 2009-11-25
hey all

i tried to install skystar2 driver but i failed

i used [http://www.linuxtv.org/wiki/index.php/TechniSat_SkyStar_2_TV_PCI_/_Sky2PC_PCI](http://www.linuxtv.org/wiki/index.php/TechniSat_SkyStar_2_TV_PCI_/_Sky2PC_PCI)

and i get
[php]root@roote:~/v4l-dvb# make 
make -C /root/v4l-dvb/v4l 
make[1]: Entering directory `/root/v4l-dvb/v4l'
scripts/make_makefile.pl
./scripts/make_kconfig.pl /lib/modules/2.6.31-15-generic/build /lib/modules/2.6.31-15-generic/build
Preparing to compile for kernel version 2.6.31

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

./scripts/make_myconfig.pl
make[1]: Leaving directory `/root/v4l-dvb/v4l'
make[1]: Entering directory `/root/v4l-dvb/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.31-15-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
Kernel build directory is /lib/modules/2.6.31-15-generic/build
make -C /lib/modules/2.6.31-15-generic/build SUBDIRS=/root/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CC [M]  /root/v4l-dvb/v4l/tuner-xc2028.o
/root/v4l-dvb/v4l/tuner-xc2028.c:55: error: 'FIRMWARE_NAME_MAX' undeclared here (not in a function)
make[3]: *** [/root/v4l-dvb/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/root/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/root/v4l-dvb/v4l'
make: *** [all] Error 2
[/php]> # lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:01.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
[php]root@roote:~# uname -a
Linux roote 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux
[/php]
i used Kaffeine to see if it is really installed but there is no dvb in Kaffeine
any1 help

---

### Post by SanderVdB on 2009-12-18
Hi,


I'm having the same problems on my system.

Did you have find already a solution for this?


Kind regards,

Sander

---

### Post by BenLuca on 2010-01-11
I get the same error.

The device worked, but then after reboot didn't work.

I think skystar 2 rev 2.8a is not supported.

The only option is to buy a supported card, see [http://www.linuxtv.org/](http://www.linuxtv.org/).

---

### Post by BenLuca on 2010-10-14
> **BenLuca said:**
> I get the same error.

The device worked, but then after reboot didn't work.

I think skystar 2 rev 2.8a is not supported.

The only option is to buy a supported card, see [http://www.linuxtv.org/](http://www.linuxtv.org/).


Hi there,
I posted this a long time ago. And it was not true, sorry.
The card works good under Ubuntu 10.04 and 10.10
out of the box.

But you can also install a proprietary driver, how to can be found here:

[http://forum.ubuntuusers.de/topic/treiber-fuer-dvb-karte-technisat-skystar2-rev/3/#post-1773333]("http://forum.ubuntuusers.de/post/1773333/")

---

