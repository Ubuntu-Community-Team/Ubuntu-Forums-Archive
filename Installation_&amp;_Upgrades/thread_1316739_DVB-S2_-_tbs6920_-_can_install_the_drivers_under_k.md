---
title: "DVB-S2 - tbs6920 - can install the drivers under kubuntu/ubuntu 9.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Vol666 on 2009-11-06
Hello
 
I have DVB-S2 PCI-E Card - TBS 6920

First of all i have to say that i have no problems installing the drivers under ubuntu and kubuntu 9.04. No problems at all with installing the drivers and watching with Kaffeine!

I have installed kubuntu 9.10 -
The problem is when i have to build and install linux-s2pi-tbs6920-8920-v23 with the commands make and make install

Under kubuntu 9.10 shows me this:
```
root@alex-desktop:~/tbs# cd linux-s2api-tbs6920-8920-v23        
root@alex-desktop:~/tbs/linux-s2api-tbs6920-8920-v23# make      
make -C /root/tbs/linux-s2api-tbs6920-8920-v23/v4l              
make[1]: Entering directory `/root/tbs/linux-s2api-tbs6920-8920-v23/v4l'
No version yet, using 2.6.31-14-generic-pae                             
make[1]: Leaving directory `/root/tbs/linux-s2api-tbs6920-8920-v23/v4l' 
make[1]: Entering directory `/root/tbs/linux-s2api-tbs6920-8920-v23/v4l'
scripts/make_makefile.pl                                                
Updating/Creating .config                                               
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

Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/root/tbs/linux-s2api-tbs6920-8920-v23/v4l'
make[1]: Entering directory `/root/tbs/linux-s2api-tbs6920-8920-v23/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.31-14-generic-pae/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
Kernel build directory is /lib/modules/2.6.31-14-generic-pae/build
make -C /lib/modules/2.6.31-14-generic-pae/build SUBDIRS=/root/tbs/linux-s2api-tbs6920-8920-v23/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic-pae'
  CC [M]  /root/tbs/linux-s2api-tbs6920-8920-v23/v4l/tuner-xc2028.o
/root/tbs/linux-s2api-tbs6920-8920-v23/v4l/tuner-xc2028.c:55: error: 'FIRMWARE_NAME_MAX' undeclared here (not in a function)
make[3]: *** [/root/tbs/linux-s2api-tbs6920-8920-v23/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/root/tbs/linux-s2api-tbs6920-8920-v23/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic-pae'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/root/tbs/linux-s2api-tbs6920-8920-v23/v4l'
make: *** [all] Error 2
```

after restart shows just this:
```
root@alex-desktop:~/tbs# cd linux-s2api-tbs6920-8920-v23
root@alex-desktop:~/tbs/linux-s2api-tbs6920-8920-v23# make
make -C /root/tbs/linux-s2api-tbs6920-8920-v23/v4l
make[1]: Entering directory `/root/tbs/linux-s2api-tbs6920-8920-v23/v4l'
creating symbolic links...
Kernel build directory is /lib/modules/2.6.31-14-generic-pae/build
make -C /lib/modules/2.6.31-14-generic-pae/build SUBDIRS=/root/tbs/linux-s2api-tbs6920-8920-v23/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic-pae'
  CC [M]  /root/tbs/linux-s2api-tbs6920-8920-v23/v4l/tuner-xc2028.o
/root/tbs/linux-s2api-tbs6920-8920-v23/v4l/tuner-xc2028.c:55: error: 'FIRMWARE_NAME_MAX' undeclared here (not in a function)
make[3]: *** [/root/tbs/linux-s2api-tbs6920-8920-v23/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/root/tbs/linux-s2api-tbs6920-8920-v23/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic-pae'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/root/tbs/linux-s2api-tbs6920-8920-v23/v4l'
make: *** [all] Error 2

```

can i fix it somehow or have to wait for a new drivers release?

Regards,
Alex

---

### Post by Vol666 on 2009-11-08
anyone?

---

### Post by joshoekstra on 2009-11-10
Did you try it using this page?
[linuxtv.org]("http://www.linuxtv.org/wiki/index.php/TBS_6920")
You need to get firmware and put it in /lib/firmware
Also, take a look at:
[kernelnewbies for 2.6.30]("http://http://kernelnewbies.org/Linux_2_6_30"), under driver >> V4L/DVB you see that your card is supported as of kernel 2.6.30, which is older than stock karmic kernel. You should be able to get away with just getting the firmware in the right place ;)

---

### Post by teacherpat on 2009-11-11
Vol666,
I have the same problem you describe.  The card was usuable under both Ubuntu 9.04 and Kubuntu 9.04 with Kaffeine.  Under Ubuntu 9.10 the drivers will not install.
There is a German forum in which there is a lot of discussion of this problem, but no resolution.  The most recent 'hopeful' post concerns the s2-liplianin treiber (driver), but the downloaded file will not extract for me.
  [http://www.vdr-portal.de/board](http://www.vdr-portal.de/board) with thread:  [B]TBS 6920 dvb-s2 pci-e.

[/B]
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /root/tbs/linux-s2api-tbs6920-8920-v23/v4l/tuner-xc2028.o
/root/tbs/linux-s2api-tbs6920-8920-v23/v4l/tuner-xc2028.c:55: error: 'FIRMWARE_NAME_MAX' undeclared here (not in a function)
make[3]: *** [/root/tbs/linux-s2api-tbs6920-8920-v23/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/root/tbs/linux-s2api-tbs6920-8920-v23/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/root/tbs/linux-s2api-tbs6920-8920-v23/v4l'
make: *** [all] Error 2"

---

### Post by Togras on 2009-11-24
there is all ready a solution available from tbs

[http://tbsdtv.eboards.tv/viewtopic.php?f=3&t=493]("http://tbsdtv.eboards.tv/viewtopic.php?f=3&t=493")

read carefully and the driver will works
```
dmesg | grep cx23885
[   10.344523] cx23885 driver version 0.0.2 loaded
[   10.344716] cx23885 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.344781] CORE cx23885[0]: subsystem: 6920:8888, board: TurboSight TBS 6920 [card=14,autodetected]
[   11.074948] cx23885_dvb_register() allocating 1 frontend(s)
[   11.074991] cx23885[0]: cx23885 based dvb card
[   11.264803] DVB: registering new adapter (cx23885[0])
[   11.264971] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   11.264978] cx23885[0]/0: found at 0000:02:00.0, rev: 2, irq: 17, latency: 0, mmio: 0xfbc00000
[   11.264984] cx23885 0000:02:00.0: setting latency timer to 64
[   11.264988] IRQ 17/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs

```
but a i have trouble while scanning for astra 19.2E because he says that he expect only one channel

---

### Post by vagca on 2010-03-07
ubuntu 9.10  mytique dvb-s2  drivers in welke map plaatsen ( in directory pasta)
email send [email]vahittinagca@hotmail.com[/email]

---

